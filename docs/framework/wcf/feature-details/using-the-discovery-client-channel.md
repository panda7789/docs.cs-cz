---
title: Použití kanálu klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 298cafe34b20a3644f967acf15f831be5b0b90ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329931"
---
# <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování
Při psaní klientských aplikací WCF musíte znát adresu koncového bodu služby, ke kterému se připojujete. V mnoha situacích adresu koncového bodu služby není znám předem nebo adresu služby mění v průběhu času. Kanálu klienta zjišťování umožňuje napsat WCF klientskou aplikaci, zadejte popis, který chcete volat služby a kanálu klienta automaticky odešle žádost o test. Pokud služba odpoví, kanálu klienta zjišťování načte adresu koncového bodu služby z odpovědi testu a použije ho k volání služby.  
  
## <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování  
 Použití kanálu klienta zjišťování, přidat instanci <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do zásobníku kanálu klienta. Případně můžete použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> se automaticky přidá do vašeho vazby, pokud není již k dispozici.  
  
> [!CAUTION]
>  Dále je doporučeno <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je nejvyšší element v zásobníku kanálu vašeho klienta. Libovolný element vazby, který se přidá nad <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musí Ujistěte se, že <xref:System.ServiceModel.ChannelFactory> nebo kanál vytvoří nepoužívá adresu koncového bodu nebo `Via` adresa (předán `CreateChannel` – metoda) protože nemůžou obsahovat správné Adresa.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Obsahuje dvě veřejné vlastnosti třídy:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, který se používá k popisu služby chcete volat.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> která určuje koncový bod zjišťování pro odesílání zpráv zjišťování.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Vlastnost vám umožní určit kontraktu služby, který hledáte, veškeré požadované rozsahy identifikátoru URI a maximální počet dob pokusí otevřít kanál. Zavoláním konstruktoru je uveden typ kontraktu <xref:System.ServiceModel.Discovery.FindCriteria>. Obor identifikátory URI mohou být přidány do <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> vlastnost. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Vlastnost vám umožní určit maximální počet výsledků, u kterých se klient pokusí připojit k. Při přijetí odpovědi testu klient se pokusí otevřít kanál pomocí adresu koncového bodu z odpovědi testu. Pokud dojde k výjimce klient přesune další test odpověď, a čekání na další odpovědi na přijmout v případě potřeby. Chcete-li to provést, dokud se úspěšně otevření kanálu nebo je dosaženo maximálního počtu výsledků pokračuje. Další informace o těchto nastaveních najdete v tématu <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Vlastnost vám umožní určit koncový bod zjišťování použití. Obvykle se jedná <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale může být libovolný platný koncový bod.  
  
 Při vytváření vazby ke komunikaci se službou, musí být přesně stejnou vazbu použít jako službu. Jediným rozdílem je, že má klient vazby <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> vrcholu zásobníku. Pokud služba používá jedna z vazeb poskytovaných systémem, vytvořte nový <xref:System.ServiceModel.Channels.CustomBinding> a předejte mu vazeb poskytovaných systémem k <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktoru. Potom můžete přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> voláním `Insert` na <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> vlastnost.  
  
 Po přidání <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> vaše vazby a nakonfigurované, můžete vytvořit instanci třídy klienta WCF, otevřete ho a volat jeho metody. Následující příklad používá kanálu klienta zjišťování pro zjišťování služby WCF, který implementuje `ICalculator` třídy (používá se v kurzu Začínáme spuštění WCF) a zavolá jeho `Add` metoda.  
  
```  
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the   
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a>Zabezpečení a kanálu klienta zjišťování  
 Při použití kanálu klienta zjišťování, dva koncové body jsou zadané. Jeden se používá pro vyhledávání zpráv, obvykle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, a druhý je koncový bod aplikace. Při implementaci zabezpečení služby, musí k zabezpečení oba koncové body věnovat pozornost. Další informace o zabezpečení najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
