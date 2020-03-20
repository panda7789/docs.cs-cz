---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: ac90a50c6fe06a643881da2889fdea308404508e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144289"
---
# <a name="nettcp-port-sharing-sample"></a>Ukázka služby Net.TCP Port Sharing
Protokol TCP/IP používá 16bitové číslo nazývané port k rozlišení připojení k více síťovým aplikacím spuštěným ve stejném počítači. Pokud aplikace naslouchá na portu, přejde do ní veškerý přenos TCP pro tento port. Jiné aplikace nemohou poslouchat na tomto portu současně.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Mnoho protokolů má standardní nebo výchozí číslo portu, které používají. Protokol HTTP například obvykle používá port TCP 80. Internetová informační služba (IIS) má naslouchací proces pro sdílení portu mezi více aplikacemi HTTP. Služba IIS naslouchá přímo na portu a předává zprávy příslušné aplikaci na základě informací uvnitř datového proudu zpráv. To umožňuje více aplikací http používat stejné číslo portu bez nutnosti soutěžit rezervovat port pro příjem zpráv.  
  
 NetTcp Port Sharing je funkce WCF (Windows Communication Foundation), která podobně umožňuje více síťovým aplikacím sdílet jeden port. Služba NetTcp Port Sharing Service přijímá připojení pomocí protokolu net.tcp a předává zprávy na základě cílové adresy.  
  
 Služba sdílení portů NetTcp není ve výchozím nastavení povolena. Před spuštěním této ukázky je nutné službu povolit ručně. Další informace naleznete v [tématu How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Pokud je služba zakázána, je při spuštění serverové aplikace vyvolána výjimka.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Sdílení portů je povoleno na <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> serveru <xref:System.ServiceModel.NetTcpBinding> nastavením <xref:System.ServiceModel.Channels.TcpTransportBindingElement> vlastnosti vazby nebo prvku vazby. Klient nemusí vědět, jak bylo sdílení portů nakonfigurováno pro jeho použití na serveru.  
  
## <a name="enabling-port-sharing"></a>Povolení sdílení portů  
 Následující kód ukazuje povolení sdílení portů na serveru. Spustí instanci `ICalculator` služby na pevném portu s náhodnou cestou IDENTIFIKÁTORURI. Přestože dvě služby mohou sdílet stejný port, jejich celkové adresy koncového bodu musí být stále jedinečné, aby služba sdílení portů NetTcp mohla směrovat zprávy do správné aplikace.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Pokud je povoleno sdílení portů, můžete službu spustit vícekrát, aniž byste měli konflikt nad číslem portu. Pokud změníte kód zakázat sdílení portů, spuštění dvou kopií služby <xref:System.ServiceModel.AddressAlreadyInUseException>má za následek druhé selhání s .  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Testovací ho klienta můžete použít ke kontrole, zda jsou zprávy správně směrovány do služeb sdílejících port.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 Každá instance služby vytiskne své jedinečné číslo a adresu. Například se může zobrazit následující text při spuštění service.exe.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Zadejte číslo služby, které se zde zobrazí při spuštění souboru client.exe.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Tuto ukázku lze spustit v konfiguraci mezi počítači změnou generované adresy, kterou klient používá. V Client.cs změňte formátovací řetězec adresy koncového bodu tak, aby odpovídal nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" IP adresou serverového počítače. Po provedení této změny je nutné znovu zkompilovat ukázku.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Povolte službu sdílení portů NetTcp, jak je popsáno dříve v úvodní části.  
  
4. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Konkrétní podrobnosti pro spuštění této ukázky jsou zahrnuty dříve v spuštění ukázkové části.  
