Liskov Subsitute prensibine göre alt seviye sınıflardan oluşan nesnelerin/sınıfların, ana(üst) sınıfın nesneleri ile yer değiştirdikleri zaman, aynı davranışı sergilemesi gerekmektedir. Türetilen sınıflar, türeyen sınıfların tüm özelliklerini kullanabilmelidir.

Varolan ve LSP’ye uymayan Kare ve dikdörtgen örneğiyle başlayalım.

LSP’ye uymayan yapı örneği;

public class Square extends Rectangle {

    @Override
    public void setWidth(int width) {
        super.setWidth(width);
        super.setHeight(width);
    }
    @Override
    public void setHeight(int height) {
        super.setHeight(height);
        super.setWidth(height);
    }
    }

Matematiksel olarak bir kareyi de bir dikdörtgen olarak kabul edebiliriz,ama bu prensibe göre yazılımda kabul edilemez.

@Test
public void testRectangleArea() throws Exception {
Rectangle rectangle = new Square();
rectangle.setWidth(20);
rectangle.setHeight(4);
assertEquals(80, rectangle.area());
}

Kareyi de beklendiği yerde dikdörtgen olarak kullanılabilir hale getirmiş olduk. Ancak böyle yaparak dikdörtgen davranışındaki beklentiyi bozuyoruz. Çünkü karenin sadece tek bir kenar bilgisi yeterlidir yada uzunluk ve en bilgisi aynı olmak durumundadır.

Matematiksel olarak karenin dikdörtgenden türediğini varsayabiliriz. Ama davranışsal olarak Kare Dikdörtgenin yerine geçmez, bu hiyerarşi Liskov prensibini (LSP) ihlal eder.O
yüzden bunu LSP'ye uygun ahle getirmemiz lazım.

Bir karenin yüksekliğinin / genişliğinin değiştirilmesi, bir dikdörtgenin yüksekliğinin / genişliğinin değiştirilmesinden daha farklı davranır. Her ikiside birer şekli temsil eder. Buradan yola çıkarak şekil interface’ini oluşturalım.

public interface Shape {
long area();
}

Kare bir şekildir o halde Square adlı bir sınıf yaratarak Shape’den implement edebiliriz.

public class Square implements Shape {
private int size;

public Square(int size) {
this.size = size;
}
@Override
public long area() {
return size \* size;
}
public void setSize(int size) {
this.size = size;
}
}

Dikdörtgen Kare ile farklı davranışlar gösterebiliyor o halde onu ayrı bir şekil olarak Rectangle adlı bir sınıf yaratıp Shape’den implement edebiliriz.

public class Rectangle implements Shape {
private int width;
private int height;

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }
    @Override
    public long area() {
        return width * height;
    }
    public void setWidth(int width) {
        this.width = width;
    }
    public void setHeight(int height) {
        this.height = height;
    }

}

Artık Kare ve Dikdörtgen kendi davranışlarına sahip oldu. Ve her biri ayrı şekil olarak kabul ediliyor. Böylece alan hesaplama her bir şekile özgü matematiksel bir işlem içerebiliyor.

public class Test {
public static void main(String[] args) {

        Shape rectangle=new Rectangle(10,5);
        System.out.println(rectangle.area()); //50

        Shape square=new Square(5);
        System.out.println(square.area()); //25
    }

}

LSP’ye uygunluk tam olarak sınıflardan beklenen davranışları karşılayabilecek bir hiyerarşi düzeni oluşturarak sınıf yapılarımızı geliştirmektir.
