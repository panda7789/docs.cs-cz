---
title: Ukázka služby Net.TCP Port Sharing
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710249"
---
# <a name="nettcp-port-sharing-sample"></a>Ukázka služby Net.TCP Port Sharing
16bitové číslo, volá se, port, protokol TCP/IP používá k rozlišení připojení k více síťových aplikací, které běží na stejném počítači. Pokud aplikace naslouchá na portu, veškerý provoz TCP pro tento port přejde k dané aplikaci. Jiné aplikace nemůže naslouchat na portu ve stejnou dobu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Mnoho protokolů mají standardní nebo výchozí číslo portu, které používají. Například protokolu HTTP obvykle využívá TCP port 80. Internetové informační služby (IIS) je sdílet mezi více aplikacemi HTTP port naslouchacího procesu. Služba IIS naslouchá na portu přímo a předává zprávy do příslušné aplikace na základě informací uvnitř datové proudy zpráv. To umožňuje používat stejné číslo portu, aniž by bylo konkurovat rezervovat port pro příjem zpráv s více aplikacemi HTTP.  
  
 Sdílení portů NetTcp je funkce Windows Communication Foundation (WCF), která podobně umožňuje více síťové aplikace sdílet jeden port. Služba sdílení portů NetTcp přijímá připojení pomocí protokol net.tcp a předává zprávy na základě jejich cílové adresy.  
  
 Služba sdílení portů NetTcp není standardně povolená. Před spuštěním této ukázky musíte ručně povolit službu. Další informace najdete v tématu [postupy: povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Pokud je služba zakázána, je vyvolána výjimka při spuštění aplikace.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Port je povoleno sdílení na serveru tak, že nastavíte <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost <xref:System.ServiceModel.NetTcpBinding> vazby nebo <xref:System.ServiceModel.Channels.TcpTransportBindingElement> element vazby. Klient nemá vědět, jak sdílení portů není nakonfigurovaná k použití na serveru.  
  
## <a name="enabling-port-sharing"></a>Povolení sdílení portů  
 Následující kód ukazuje povolení sdílení portu na serveru. Spustí instanci `ICalculator` služby na pevný port se náhodný cesty identifikátoru URI. I v případě, že dvě služby můžou sdílet stejný port, jejich celkové adresy koncových bodů i nadále musí být jedinečný tak, aby služba Sdílení portů NetTcp může směrovat zprávy do správné aplikace.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 S povoleno sdílení portu, můžete spustit službu vícekrát bez nutnosti konflikt přes číslo portu. Pokud změníte kód a zakázat sdílení portů, spouštění dvě kopie výsledků služby v druhé selhání se <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Testovacího klienta můžete použít ke kontrole, že zprávy jsou správně směrovat do služby Sdílení portu.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
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

 Každá instance služby vytiskne jeho jedinečné číslo a adresu. Při spuštění service.exe, například může zobrazit následující text.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Zadejte číslo, které se tady zobrazí při spuštění client.exe.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka můžete spustit v konfiguraci mezi počítači změnou vygenerovaný adresy, které klient používá. V Client.cs změňte řetězec formátu adresa koncového bodu tak, aby odpovídala nové adresu služby. Všechny odkazy na "localhost" nahraďte IP adresu počítače serveru. Po provedení této změny je potřeba překompilovat vzorku.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Povolte službu NetTcp Port Sharing podle předchozích pokynů v úvodní části.  
  
4.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Konkrétní podrobnosti o spuštěním této ukázky jsou dříve součástí běžící ukázkový oddíl.  
  
## <a name="see-also"></a>Viz také
