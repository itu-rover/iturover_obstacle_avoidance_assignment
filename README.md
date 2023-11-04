<p align="center">
  <img src="https://github.com/itu-rover/iturover_obstacle_avoidance_assignment/assets/99661459/ac4adfa5-b237-4c0e-9f1e-56532de83b65" alt="iturover" width="300"/>
</p>
<p align="center">
  <em>My battery is low and it's getting dark.</em>
</p>


# ITU Rover Obstacle Avoidance Robot Assignment

Bu ödevde göreviniz Turtlebot simülasyonu kullanarak reaktif şekilde engelden kaçınma algoritması geliştirmek olacaktır. Robot önüne çıkan engellerden _/scan_ topic'inden gelen [LaserScan](https://docs.ros.org/en/api/sensor_msgs/html/msg/LaserScan.html) mesaj türündeki veriyi kullanarak kaçınmalıdır. Robot etrafındaki engelleri tespit etmek için lazer tarayıcı kullanmalı ve aşağıdaki şekilde hareket etmelidir.

<br>
<br>




* Hızını önündeki engel durumuna göre değiştirmeli.
* Önündeki engellere göre uzaktan manevra yapmalı.
* Robotun hareketi boyunca hızının aynı olması ve robot süpürgeler gibi durduğu yerde dönmesi istenmemektedir.
* Smooth bir hareket gözlenmelidir.


<br>
<br>




<p align="center">
  <img src="https://github.com/itu-rover/iturover_obstacle_avoidance_assignment/assets/99661459/e3828def-fe18-4531-a2a4-796c0e6797b1" alt="harita" width="1200"/>
</p>
<p align="center">
  <em>Robotun hareketini gerçekleştireceği parkur</em>
</p>
<br>
<br>




Robotun hareket süresi 60 saniyedir. Bu süre boyunca koridorda başlangıç noktasından olabildiğince uzaklaşmalıdır. 60 saniyenin sonrasında simülasyon ortamının ışığı söndürülmeli ve robot hareketini sonladırmalıdır. Robotun hareketi aşağıdaki örnekteki gbi olmalıdır.

<br>
<br>






https://github.com/itu-rover/iturover_obstacle_avoidance_assignment/assets/99661459/6ad153ed-4203-452b-babd-e2b1d091dcd2






<br>
<br>



Ödevle ilgili daha fazla bilgiye ve yardımcı olacak kaynaklara aşağıdan ulaşabilirsiniz.

# Kurulum

Bir workspace oluşturun.

```
mkdir ~/rover_ws
cd ~/rover_ws
catkin_init_workspace
mkdir src
```

Bu paketi klonlayıp derleyin.

```
cd ~/rover_ws/src
git clone https://github.com/itu-rover/iturover_obstacle_avoidance_assignment
cd ..
catkin build
```
İçerisinde launch dosyası olan yeni bir paket oluşturun.

```
cd ~/rover_ws/src
catkin_create_pkg reactive_robot std_msgs rospy geometry_msgs message_generation
cd reactive_robot
mkdir launch
```


# Kullanım

Turtlebot simülasyonunu kullanmak için gerekli paketleri kurun.

`
sudo apt install ros-noetic-turtlebot3-simulations
`

Gazebo ve RViz'i çalıştırmak için aşağıdaki komutu terminal yardımıyla çalıştırın.

`
roslaunch reactive_robot_sim reactive_robot_sim.launch
`


## İsterler ve Kısıtlamalar
<br>
<br>




* Robot bir komut ile harekete geçmelidir.
* Robot harekete geçtikten sonra 60 saniye hareket etmelidir.
* Robot, hareketi esnasında **lazer tarayıcadan gelen veriyi kullanarak** herhangi bir engele çarpmadan hareket etmelidir.
* 60 saniyelik sürenin sonunda robot hareketini sonlandırmalı, _/scan_ topic'inden unsubscribe olmalı ve node kapanmalıdır.
* 60 saniyelik sürenin sonunda Gazebo ortamındaki _sun_ adlı ışık Gazebo service'i olan _DeleteLight_ yardımıyla kaldırılmalıdır. 
* Robotun hareketindeki değişimler _rospy.loginfo_ yardımıyla terminalde gösterilmelidir. Örneğin: _Started rotating left._ Her değişim için yapmayı unutmayınız.
* Node ile ilgili bilgiler _rospy.loginfo_ yardımıyla terminalde gösterilmelidir. Örneğin: _Time limit reached. Stopping..._
* Script'iniz ve simülasyon ortamı aynı anda launch dosyası yardımıyla çalıştırılmalıdır.
* Launch dosyasının ismi reactive_robot.launch_ olmalıdır.
* Robotun hareketini ayarlamak için kullanacağınız değişkenlerin değerleri oluşturacağınız launch dosyasından çekilmelidir.
* Kodunuz yorum satırlarıyla açıklanmalıdır.

<br>
<br>




# Ayrıca bakınız

* https://wiki.ros.org/ROS/Tutorials
* https://wiki.ros.org/Robots/TIAGo/Tutorials/motions/cmd_vel
