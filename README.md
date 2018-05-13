<?xml version="1.0"?>
<launch>
  <!--<node pkg="xv_11_laser_driver" type="neato_laser_publisher" name="xv_11_node">
    <param name="port" value="/dev/ttyUSB0"/>
    <param name="firmware_version" value="2"/>
    <param name="frame_id" value="laser"/>
  </node>-->
  <node pkg="tf" type="static_transform_publisher" name="map_to_odom" args="0.0 0.0 0.0 0 0 0.0 /odom /base_link 10"/>
  <node pkg="tf" type="static_transform_publisher" name="base_frame_laser" args="0 0 0 0 0 0 /base_link /laser 10"/>
  <!--<node pkg="rviz" type="rviz" name="rviz" 
    args="-d $(find hector_slam_launch)/rviz_cfg/mapping_demo.rviz"/>-->
  <include file="$(find hector_mapping)/launch/mapping_default.launch"/> 
  <node pkg="rviz" type="rviz" name="rviz" args="-d rviz_cfg.rviz"/>
  <include file="$(find hector_geotiff)/launch/geotiff_mapper.launch"/>
</launch>

