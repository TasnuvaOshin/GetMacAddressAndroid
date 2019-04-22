# GetMacAddressAndroid
Simply Get the Mac Address of User Device Android
#you can simply call this method and get the MacAddress of your user Device . for more you can check out the device Module File in my repository . 



          public static String getMacAddress() {
              try {
                  String interfaceName = "wlan0";
                  List<NetworkInterface> interfaces = Collections.list(NetworkInterface.getNetworkInterfaces());
                  for (NetworkInterface intf : interfaces) {
                      if (!intf.getName().equalsIgnoreCase(interfaceName)) {
                          continue;
                      }

                      byte[] mac = intf.getHardwareAddress();
                      if (mac == null) {
                          return "";
                      }

                      StringBuilder buf = new StringBuilder();
                      for (byte aMac : mac) {
                          buf.append(String.format("%02X:", aMac));
                      }
                      if (buf.length() > 0) {
                          buf.deleteCharAt(buf.length() - 1);
                      }
                      return buf.toString();
                  }
              } catch (Exception ex) {
              } 
              return "";
          }
          
          
          
          
  #make sure You have this in your Manifest File 
  
  
      <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
