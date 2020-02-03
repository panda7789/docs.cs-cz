---
title: Základní ukázka
ms.date: 03/30/2017
ms.assetid: c1910bc1-3d0a-4fa6-b12a-4ed6fe759620
ms.openlocfilehash: 2ea5af0a1c05b5632632b2619c0ee4813696d2fc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738179"
---
# <a name="basic-sample"></a>Základní ukázka

V této ukázce se dozvíte, jak nastavit službu jako zjistitelnou a jak hledat a volat zjistitelnou službu. Tato ukázka se skládá ze dvou projektů: služby a klienta.

> [!NOTE]
> Tato ukázka implementuje zjišťování v kódu.  Ukázku, která implementuje zjišťování v konfiguraci, najdete v tématu [Configuration](../../../../docs/framework/wcf/samples/configuration-sample.md).

## <a name="service"></a>Služba

Toto je jednoduchá implementace služby Kalkulačka. Kód související se zjišťováním najdete v `Main`, kde se do hostitele služby přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a přidá se <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jak je znázorněno v následujícím kódu.

```csharp
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

Klient nástroje používá <xref:System.ServiceModel.Discovery.DynamicEndpoint> k vyhledání služby. <xref:System.ServiceModel.Discovery.DynamicEndpoint>standardního koncového bodu při otevření klienta vyřeší koncový bod služby. V takovém případě <xref:System.ServiceModel.Discovery.DynamicEndpoint> službu vyhledá na základě kontraktu služby. <xref:System.ServiceModel.Discovery.DynamicEndpoint> provede hledání <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve výchozím nastavení. Jakmile nalezne koncový bod služby, klient se k této službě připojí přes určenou vazbu.

```csharp
public static void Main()
{
   DynamicEndpoint dynamicEndpoint = new DynamicEndpoint( ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());
   // ...
}
```

Klient definuje metodu nazvanou `InvokeCalculatorService`, která používá třídu <xref:System.ServiceModel.Discovery.DiscoveryClient> k hledání služeb. <xref:System.ServiceModel.Discovery.DynamicEndpoint> dědí z <xref:System.ServiceModel.Description.ServiceEndpoint>, takže jej lze předat metodě `InvokeCalculatorService`. V příkladu se pak pomocí <xref:System.ServiceModel.Discovery.DynamicEndpoint> vytvoří instance `CalculatorServiceClient` a zavolá různé operace služby kalkulačky.

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

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné seznamy ACL adres URL. Další informace najdete v tématu [Konfigurace HTTP a HTTPS](../feature-details/configuring-http-and-https.md). Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Pomocí sady Visual Studio 2012 otevřete základní. sln a sestavte ukázku.

3. Spusťte aplikaci Service. exe.

4. Po spuštění služby spusťte soubor Client. exe.

5. Pozor, aby klient mohl najít službu bez znalosti její adresy.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Basic`
