---
title: Ukázka služby Net.TCP Port Sharing
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0db4148f9be6db97dec2b8b680dad56171106b2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="nettcp-port-sharing-sample"></a>Ukázka služby Net.TCP Port Sharing
Protokol TCP/IP používá 16bitové čísla, který se nazývá port, k odlišení připojení k několika síťových aplikací, které jsou spuštěné na stejném počítači. Pokud aplikace naslouchá na portu, pak všechny přenosy TCP pro tento port přejde k dané aplikaci. Ostatní aplikace nemůže naslouchat na tomto portu ve stejnou dobu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Mnoho protokolů mají standard nebo výchozí číslo portu, které používají. Například protokol HTTP se většinou používá TCP port 80. Internetové informační služby (IIS) má naslouchací proces sdílení portů mezi více aplikacemi HTTP. Služba IIS naslouchá na portu přímo a přeposílá zprávy na příslušnou aplikaci na základě informací uvnitř datového proudu zpráv. To umožňuje používat stejné číslo portu bez nutnosti pokouší tak, aby vyhradil port pro příjem zprávy více aplikacemi HTTP.  
  
 Sdílení portů NetTcp je [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]funkce, která podobně umožňuje více síťových aplikací sdílet jeden port. Služba sdílení portů NetTcp přijímá připojení pomocí protokolu net.tcp a přeposílá zprávy na základě jejich cílové adresy.  
  
 Služba sdílení portů NetTcp není povolena ve výchozím nastavení. Před spuštěním této ukázce, je nutné ručně povolit službu. Další informace najdete v tématu [postupy: povolení služby Sdílení portů Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Pokud je služba zakázána, je vyvolána výjimka při spuštění aplikace serveru.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Sdílení portů je na serveru povoleno nastavením <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> vlastnost <xref:System.ServiceModel.NetTcpBinding> vazba nebo <xref:System.ServiceModel.Channels.TcpTransportBindingElement> prvku vazby. Klient nemá vědět, jak sdílení portů byl nakonfigurován pro použití na serveru.  
  
## <a name="enabling-port-sharing"></a>Povolení sdílení portů  
 Následující kód ukazuje, povolení sdílení portů na serveru. Spustí instanci `ICalculator` na pevný port s náhodných cestou URI. I když dvě služby můžete sdílet stejný port, jejich celkový adresy koncových bodů stále musí být jedinečný, aby služba Sdílení portů NetTcp může směrovat zprávy správnou aplikaci.  

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

 S sdílení portů povolené, můžete spustit službu vícekrát bez došlo ke konfliktu u číslo portu. Pokud změníte kód zakázat sdílení portů, spuštění dvě kopie výsledků služby v druhé selhání s <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Chcete-li zkontrolovat, že zprávy jsou správně směrované na sdílení port služby můžete testovacího klienta.  

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

 Každá instance služby vytiskne jeho jedinečné číslo a adresu. Když spustíte service.exe například může zobrazit následující text.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Zadejte číslo služby, kterou tady vidíte při spuštění client.exe.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Tato ukázka se může spouštět ve konfigurací mezi počítači změnou generované adresy, které klient používá. V Client.cs změňte řetězec formátu adresa koncového bodu tak, aby odpovídala nové adresy vaší služby. Nahradí všechny odkazy na "localhost" IP adresu počítače serveru. Po provedení této změny je potřeba překompilovat vzorku.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Povolte službu NetTcp Port Sharing výše popsané v části Úvod.  
  
4.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Konkrétní podrobnosti ke spuštění této ukázce jsou dříve součástí spuštění ukázkový oddíl.  
  
## <a name="see-also"></a>Viz také
