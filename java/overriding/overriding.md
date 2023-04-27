# 메서드 오버라이딩 (overriding)
  
## overriding이란?
  - `override` ⓥ덮어쓰다
  - 상속받은 조상의 메서드를 자신에 맞게 `변경, 덮어쓰는` 것 

## 오버라이딩의 조건 
- 선언부가 조상 클래스의 메서드와 일치해야 한다.
  - `선언부(동일한 리턴타입 / 메소드 이름 / 매개변수)`
  - `구현부`만 변경가능 (선언부 변경불가)
  
- `접근 제어자`를 조상 클래스의 메서드보다 `좁은 범위`로 변경할 수 없다.

    ![toString in the object class](/img/overriding/object-toString.jpg)

    Object클래스 toString()는 `public` 접근 제어자로 되어 있기 때문에 `private`로 지정을 한다면 아래의 그림처럼 컴파일 오류가 나는 것을 볼 수 있다.
    ![attempting to assign weaker access privileges ('private'); was 'public](/img/overriding/attempting-to%20assign-weaker%20access-privileges('private').jpg)

- 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다.(같거나 조상클래스보다 적어야 함)
![parent overridden method does not throw](/img/overriding/parent-overridden-method-does-not-throw.jpg)

## 예제 1
```
package me.javahjungsuk.overriding;
import java.util.Objects;

class Point {
    int x;
    int y;

    public void getLocation() {
        System.out.println("x: " + x + " y:" + y);
    }
}

class Point3D extends Point {
    int z;

    @Override
    public void getLocation() {
        System.out.println("x:" + x + " y:" + y + " z:" + z);
    }
}

public class OverridingTest {
    public static void main(String[] args) {
        Point3D point3D = new Point3D();
        point3D.x = 3;
        point3D.y = 5;
        point3D.z = 8;
        point3D.getLocation();
    }
}

```
출력
```
x:3 y:5 z:8
```
- 상속이 안된 것이냐? 아니다. 상속이 됐는데 두개 중 overriding한게 호출이 된 것 
- 오버라이딩 했다고 해서 상속을 안받는 것이 아니고 받긴 받는데 조상꺼를 안 쓰고 자손것을 쓰는 것을 의미한다.

![practice1-overriding](/img/overriding/practice1-overriding.jpg)


## 예제 2
```
import java.util.Objects;

class HealthInfo {
    protected String name;
    protected int height;
    protected int weight;

    public HealthInfo() {}
    public HealthInfo(String name, int height, int weight) {
        this.name = name;
        this.height = height;
        this.weight = weight;
    }

    public String getName() {
        return name;
    }

    public int getHeight() {
        return height;
    }

    public int getWeight() {
        return weight;
    }

    public void showInfo() {
        System.out.println(name + "님의 신장은 " + height + "cm이고  몸무게는" + weight + "kg 입니다.");
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        HealthInfo that = (HealthInfo) obj;
        return name.equals(that.name)
                && height == that.height
                && weight == that.weight;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, height, weight);
    }

    @Override
    public String toString() {
        return "HealthInfo{" +
                "name=" + name +
                ", height='" + height + '\'' +
                ", weight='" + weight + '\'' +
                '}';
    }
}

class HealthRate extends HealthInfo  {

    HealthRate(String name, int height, int weight) {
        super(name, height, weight);
    }

    public double standardWeight() {
        return (this.height - 100) * 0.9;
    }

    public double getRate() {
        return (this.weight - standardWeight()) / standardWeight() * 100;
    }

    public String status() {
        double rate = getRate();
        if (rate < 10) {
            return "정상";
        } else if (rate < 20) {
            return "과체중";
        } else {
            return "비만";
        }
    }

    @Override
    public void showInfo() {
        super.showInfo();
        System.out.println(" => " + status() + "입니다.");
    }
}

public class OverridingTest {
    public static void main(String[] args) {

        HealthRate healthRate = new HealthRate("dpdmstjs", 170, 48);
        healthRate.showInfo();

    }
}
```
![practice2-constructor](/img/overriding/practice2-constructor.jpg)

![practice2-showInfo-overriding](/img/overriding/practice2-showInfo-overriding.jpg)
