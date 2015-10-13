# BluetoothSample.WPF
WPF app to send data through Bluetooth using async connection and threads to monitor connection. based on saramgsilva's work (github: https://github.com/saramgsilva/BluetoothSampleUsing32feet.Net).

# Changes:

Version 0.9
Connection and Sending actions are in separate methods; sometimes some exceptions could occur when connect a device and then  write in the bluetoothStream if those methods are in the same async task. This is because the connection action is executed, the device response the connection request, but the bluetoothStream is not ready to use since the connection is not 'totally complete'

To avoid this problem, the following methodes were implemented:

# DeviceConnection(Device device)  
- Create a connection for the selected device.

# bool CheckConnection()          
- Check if the device is connected and bluetoothStream ready.

#SendAsync(Device device, string content)
- Send the data, only available when CheckConnection() = true.
 
#CheckDeviceConnection()
- As DeviceConnection is execute on demand when the user wants to connect, this method runs o a thread that keeps monitoring the status of the connection, updating CheckConnection and allowing SendAsync to avoid errors.

Any question or recomendation feel free to write me to: 
williamkodi@gmail.com

