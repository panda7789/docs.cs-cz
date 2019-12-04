---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: e7a814dcdc027980f70ec90e384f3ec2f74b364d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714707"
---
# <a name="nettcp-port-sharing-sample"></a>Ukázka služby Net.TCP Port Sharing
Protokol TCP/IP používá 16bitové číslo označované jako port pro odlišení připojení k více síťovým aplikacím běžícím ve stejném počítači. Pokud aplikace naslouchá na portu, pak všechny přenosy TCP pro daný port přecházejí do této aplikace. Jiné aplikace nemohou na tomto portu současně naslouchat.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Mnoho protokolů má standardní nebo výchozí číslo portu, které používají. Například protokol HTTP obvykle používá port TCP 80. Internetová informační služba (IIS) má naslouchací proces ke sdílení portu mezi více aplikacemi HTTP. Služba IIS naslouchá přímo na portu a přesměruje zprávy do příslušné aplikace na základě informací uvnitř datového proudu zpráv. To umožňuje více aplikacím HTTP používat stejné číslo portu, aniž by bylo nutné soutěžit o rezervaci portu pro příjem zpráv.  
  
 Sdílení portů NetTcp je funkce Windows Communication Foundation (WCF), která podobně umožňuje více síťovým aplikacím sdílet jeden port. Služba sdílení portů NetTcp akceptuje připojení pomocí protokolu net. TCP a přepošle zprávy na základě jejich cílové adresy.  
  
 Služba sdílení portů NetTcp není ve výchozím nastavení povolená. Před spuštěním této ukázky musíte ručně povolit službu. Další informace najdete v tématu [Postup: povolení služby sdílení portů Net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Pokud je služba zakázaná, vyvolá se při spuštění serverové aplikace výjimka.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Sdílení portů je na serveru povoleno nastavením vlastnosti <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> <xref:System.ServiceModel.NetTcpBinding> vazby nebo elementu vazby <xref:System.ServiceModel.Channels.TcpTransportBindingElement>. Klient nemusí znát způsob, jakým bylo sdílení portů nakonfigurováno pro jeho použití na serveru.  
  
## <a name="enabling-port-sharing"></a>Povolení sdílení portů  
 Následující kód ukazuje povolení sdílení portů na serveru. Spustí instanci služby `ICalculator` na pevném portu s náhodným umístěním URI. I když můžou dva služby sdílet stejný port, musí být jejich celkový koncový bod stále jedinečný, aby služba sdílení portů NetTcp mohla směrovat zprávy do správné aplikace.  

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

 Když je povolené sdílení portů, můžete službu spustit několikrát, aniž by došlo ke konfliktu s číslem portu. Pokud změníte kód tak, aby se zakázalo sdílení portů, spuštění dvou kopií služby má za následek selhání s <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Testovacího klienta můžete použít ke kontrole, zda jsou zprávy správně směrovány na služby sdílející daný port.  

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

 Každá instance služby vytiskne své jedinečné číslo a adresu. Při spuštění souboru Service. exe se například může zobrazit následující text.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Zadejte číslo služby, které se zobrazí, když spustíte soubor Client. exe.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Tuto ukázku můžete spustit v konfiguraci mezi počítači změnou vygenerované adresy, kterou klient používá. V Client.cs změňte řetězec formátu adresy koncového bodu tak, aby odpovídal nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" adresou IP počítače serveru. Po provedení této změny je nutné ukázku znovu zkompilovat.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Povolte službu sdílení portů NetTcp, jak je popsáno výše v části Úvod.  
  
4. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Konkrétní podrobnosti pro spuštění této ukázky jsou uvedeny dříve v části spuštění ukázkového oddílu.  
