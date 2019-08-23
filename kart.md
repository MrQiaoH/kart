<table>
	<tr>
		<td >类</td>
		<td>项</td>
		<td>读取/设置(1/0)</td>	
		<td>6字节无效数据</td>	
		<td colspan = "3"> 参数(按顺序排列)</td>	
	</tr>
	<tr>
		<td rowspan = "3">版本(0x01) </td>
			<td>设备型号(0x01)</td>
			<td>1</td>
			<td>-</td>
			<td>字符串(byte[])</td>	
			<td> </td>	
			<td> </td>	
	</tr>
	<tr>
			<td>硬件版本(0x01)</td>
			<td>1</td>
			<td>-</td>
			<td>字符串(byte[])</td>
			<td> </td>	
			<td> </td>	
	</tr>	
	<tr>
			<td>软件版本(0x01))</td>
			<td>1</td>
			<td>-</td>
			<td>字符串(byte[])</td>
			<td> </td>	
			<td> </td>	
	</tr>	
	<tr>
		<td rowspan = "2">发动机(0x11)</td>
			<td>发动机转速倍率(0x01)</td>
			<td>1/0</td>
			<td>-</td>
			<td>倍率(rpm*n)(uint8)</td>	
			<td> </td>	
			<td> </td>	
	</tr>	
	<tr> 
			<td>发动机采样频率(0x02)</td>
			<td>1/0</td>
			<td>-</td>
			<td>频率(10,20,50,100)(uint16)</td>	
			<td> </td>	
			<td> </td>	
	</tr>	
	<tr>
		<td rowspan = "4">温度采集(0x12)</td>
			<td>内部温度(0x01)</td>
			<td>1/0</td>
			<td>-</td>
			<td>温度值(int16)</td>	
			<td> </td>	
			<td> </td>	
	</tr>	
	<tr>
			<td>冷却液温度(0x11)</td>
			<td>1/0</td>
			<td>-</td>
			<td>最低温度(int16)</td>
			<td>最高温度(int16)</td>	
			<td>报警温度(int16)</td>				
	</tr>	
	<tr>
			<td>缸盖温度(0x12)</td>
			<td>1/0</td>
			<td>-</td>
			<td>最低温度(int16)</td>
			<td>最高温度(int16)</td>	
			<td>报警温度(int16)</td>	
	</tr>	
	<tr>
			<td>排气温度(0x13)</td>
			<td>1/0</td>
			<td>-</td>
			<td>最低温度(int16)</td>
			<td>最高温度(int16)</td>	
			<td>报警温度(int16)</td>	
	</tr>
	<tr>
		<td rowspan = "2">工作模式(0x81)</td>
			<td>进入引导(0x01) </td>
			<td>0</td>
			<td>-</td>
			<td> </td>
			<td> </td>				
			<td> </td>	
	</tr>	
	<tr>
			<td>进入固件升级(0x12) </td>
			<td>0</td>
			<td>-</td>
			<td> </td>
			<td> </td>				
			<td> </td>	
	</tr>	
	<tr>
		<td rowspan = "3">固件升级(0x82)</td>
			<td>最大数据包大小(0x11) </td>
			<td>1</td>
			<td>-</td>
			<td>数据包大小(uint32)</td>	
			<td>错误传输次数(uint8)</td>
			<td> </td>				
	</tr>
	<tr>
			<td>文件参数(0x12)</td>
			<td>0</td>
			<td>-</td>
			<td>文件大小(uint32)</td>	
			<td>校验码(uint8)</td>	
			<td> </td>	
	</tr>
	<tr>
			<td>数据包参数(0x13)</td>
			<td>0</td>
			<td>-</td>
			<td>数据包大小(uint32)</td>	
			<td>校验码(uint8)</td>	
			<td> </td>				
	</tr>		
	<tr>
		<td rowspan = "5">计时器(0xA1)</td>
			<td>总开机时间(0x10) </td>
			<td>1</td>
			<td>-</td>
			<td>分钟数(uint32)</td>	
			<td> </td>		
			<td> </td>				
	</tr>
	<tr>
			<td>保养计时器(0x11)</td>
			<td>1/0</td>
			<td>-</td>
			<td>开关(uint8)</td>	
			<td>分钟数(uint32)</td>	
			<td>保养周期(uint32)</td>	
	</tr>	
	<tr>
			<td>计时器1(0x21)</td>
			<td>1/0</td>
			<td>-</td>
			<td>开关(uint8)</td>	
			<td>分钟数(uint32)</td>	
			<td> </td>	
	</tr>	
	<tr>
			<td>计时器2(0x22)</td>
			<td>1/0</td>
			<td>-</td>
			<td>开关(uint8)</td>
			<td>分钟数(uint32)</td>	
			<td> </td>				
	</tr>	
	<tr>
			<td>计时器3(0x23)</td>
			<td>1/0</td>
			<td>-</td>
			<td>开关(uint8)</td>
			<td>分钟数(uint32)</td>	
			<td> </td>				
	</tr>		
</table>
Engine.Temper 包含 **UNIX时间戳** / **毫秒**  / **冷却液温度** / **缸盖温度** / **排气管温度**  
数据排列方式如下：

Byte Index | Content             | Type(bytes) | Comment
---        | ---                 | ---         | ---
0          | Index               | byte(1)     | = 0x22，表示该数据包是Engine.Temper
1          | unix timestamp      | uint32(4)   | UNIX时间戳，从*1970/1/1*以UTC-0作为时间起点
5          | millsecond          | uint16(2)   | 毫秒数，例如： 0, 100 ,200, ... 900 或者更高经度: 50, 150, 950等
7          | water temp          | float(4)    | 冷却液温度 单位：摄氏度
11         | cylinder head temp  | float(4)    | 缸盖温度 单位：摄氏度
15         | exhaust gas temp    | float(4)    | 排气管温度 单位：摄氏度

### Device

Bean设备信息包含 **电池电量**  
数据排列方式如下：

Byte Index | Content             | Type(bytes) | Comment
---        | ---                 | ---         | ---
0          | Index               | byte(1)     | = 0xA1，表示该数据包是Device
1          | battery percent     | int8(1)     | 电池电量百分比，电量错误-1

