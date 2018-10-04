---
title: Základní ukázka
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 29edc8acb0293210e66e31660e3215220440fbae
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580313"
---
# <a name="basic-sample"></a>Základní ukázka
Tato ukázka předvádí, jak je nechat zjistitelné služby a jak vyhledat a volat zjistitelné služby. Tento příklad se skládá ze dvou projektů: klienta a služby.

> [!NOTE]
>  Tato ukázka implementuje zjišťování v kódu.  Ukázku, která implementuje zjišťování v konfiguraci najdete v tématu [konfigurace](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Služba  
 Toto je implementace služby jednoduchou kalkulačku. Zjišťování týkající se kód lze nalézt v `Main` kde <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se přidá k hostiteli služby a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se přidá, jak je znázorněno v následujícím kódu.  
  
```  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new   
      WSHttpBinding(), String.Empty);  
  
    // Make the service discoverable over UDP multicast  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Klient  
 Klient použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> najít službu. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Je standardní koncový bod, řeší koncový bod služby při otevření klienta. V takovém případě <xref:System.ServiceModel.Discovery.DynamicEndpoint> vyhledá službu, kterou kontrakt služby. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Provádí hledání nad <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve výchozím nastavení. Jakmile je možné vyhledat koncového bodu služby, klient se připojí k této službě přes určenou vazbu.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Klient definuje metodu nazvanou `InvokeCalculatorService` , která používá <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy pro vyhledání služeb. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Dědí z <xref:System.ServiceModel.Description.ServiceEndpoint>, takže mohou být předány `InvokeCalculatorService` metody. Příklad poté použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vytvoření instance `CalculatorServiceClient` a volá různé operace objektu službu kalkulačky.  
  
```csharp  
static void InvokeCalculatorService(ServiceEndpoint serviceEndpoint)  
{  
   // Create a client  
   CalculatorServiceClient client = new CalculatorServiceClient(serviceEndpoint);  
  
   Console.WriteLine("Invoking CalculatorService");  
   Console.WriteLine();  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Subtract service operation.  
   result = client.Subtract(value1, value2);  
   Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Multiply service operation.  
   result = client.Multiply(value1, value2);  
   Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
   // Call the Divide service operation.  
   result = client.Divide(value1, value2);  
   Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
   Console.WriteLine();  
  
   //Closing the client gracefully closes the connection and cleans up resources  
   client.Close();  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Tato ukázka používá koncové body HTTP a pokud chcete tuto ukázku spustit, musíte přidat správné seznamy ACL adresy URL. Další informace najdete v tématu [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL. Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Pomocí sady Visual Studio 2012, otevřete Basic.sln a sestavit ukázku.  
  
3.  Spusťte aplikaci service.exe.  
  
4.  Po spuštění služby, spusťte client.exe.  
  
5.  Podívejte se, že byl klient nemůže najít službu bez znalosti jeho adresu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Viz také
