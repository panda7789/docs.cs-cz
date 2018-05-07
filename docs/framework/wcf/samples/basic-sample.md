---
title: Základní ukázka
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 67c626dfa511251043da81e025aab20578be3016
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="basic-sample"></a>Základní ukázka
Tento příklad ukazuje, jak zjistitelnost služby a jak k hledání a volání zjistitelný služby. Tato ukázka se skládá ze dvou projektů: klienta a služby.  
  
> [!NOTE]
>  Tato ukázka implementuje zjišťování v kódu.  Příklad, který implementuje zjišťování v konfiguraci, najdete v části [konfigurace](../../../../docs/framework/wcf/samples/configuration-sample.md).  
  
## <a name="service"></a>Služba  
 Toto je jednoduchá kalkulačky implementace služby. Zjišťování související kód lze nalézt v `Main` kde <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se přidá do hostitele služby a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> se přidá, jak je znázorněno v následujícím kódu.  
  
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
 Klient použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> najít službu. <xref:System.ServiceModel.Discovery.DynamicEndpoint>, Koncový bod standardní řeší koncový bod služby v případě, že klient je otevřen. V takovém případě <xref:System.ServiceModel.Discovery.DynamicEndpoint> hledá služby založené na kontrakt služby. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Provádí hledání přes <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve výchozím nastavení. Jakmile je možné vyhledat koncového bodu služby, klient připojí k této službě přes Zadaná vazba.  
  
```csharp  
public static void Main()  
{  
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
   // ...  
}              
```  
  
 Definuje metodu s názvem klient `InvokeCalculatorService` používající <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy pro vyhledání služeb. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Dědí z <xref:System.ServiceModel.Description.ServiceEndpoint>, takže může být předán `InvokeCalculatorService` metoda. V příkladu se pak použije <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vytvoření instance `CalculatorServiceClient` a volá různých operací službu kalkulačky.  
  
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
  
1.  Tato ukázka používá koncových bodů protokolu HTTP a pokud chcete tuto ukázku spustit, musí být přidán správné seznamy ACL adresy URL. Další informace najdete v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353). Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL. Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete Basic.sln a sestavit ukázku.  
  
3.  Spusťte aplikaci service.exe.  
  
4.  Po spuštění služby, spusťte client.exe.  
  
5.  Sledujte, aby bylo možné najít službu, aniž by věděly, jeho adresu klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`  
  
## <a name="see-also"></a>Viz také
