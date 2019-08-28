---
title: Použití kanálu klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 3b6bb38298b47b822a15fee92038a1d6beb15df3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045253"
---
# <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování
Při psaní klientské aplikace WCF potřebujete znát adresu koncového bodu služby, kterou voláte. V mnoha případech adresa koncového bodu služby není známá předem nebo se adresa služby mění v průběhu času. Kanál klienta zjišťování umožňuje napsat aplikaci klienta WCF, popsat službu, kterou chcete volat, a kanál klienta automaticky odešle požadavek testu. Když služba odpoví, kanál klienta zjišťování získá adresu koncového bodu pro službu z odpovědi sondy a použije ji k volání služby.  
  
## <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování  
 Chcete-li použít kanál klienta zjišťování, přidejte instanci <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do zásobníku kanálu klienta. Případně můžete použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> a a automaticky přidat do vazby, pokud ještě neexistují.  
  
> [!CAUTION]
> Doporučuje se, aby <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> byl prvek v zásobníku kanálů klienta nejvíce nahoře. Libovolný prvek vazby, který je <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> přidán nad, musí zajistit <xref:System.ServiceModel.ChannelFactory> , aby kanál nebo, který vytvořil, nepoužil adresu nebo `Via` adresu koncového bodu (předaný `CreateChannel` metodě), protože nemusí obsahovat správné adresáře.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Třída obsahuje dvě veřejné vlastnosti:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, který se používá k popisu služby, kterou chcete volat.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>Určuje koncový bod zjišťování, do kterého se mají odesílat zprávy zjišťování.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Vlastnost umožňuje zadat kontrakt služby, který hledáte, všechny požadované identifikátory URI oboru a maximální počet času, který se má pokusit otevřít kanál. Typ kontraktu je určen voláním konstruktoru <xref:System.ServiceModel.Discovery.FindCriteria>. Do <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> vlastnosti lze přidat identifikátory URI oboru. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Vlastnost umožňuje určit maximální počet výsledků, ke kterým se klient pokusí připojit. Když se přijme odpověď testu, klient se pokusí otevřít kanál pomocí adresy koncového bodu z odpovědi testu. Pokud dojde k výjimce, klient přejde k další reakci testu, která čeká na přijetí dalších odpovědí v případě potřeby. I nadále to bude pokračovat, dokud se kanál úspěšně neotevře nebo dokud nedosáhnete maximálního počtu výsledků. Další informace o těchto nastaveních naleznete v <xref:System.ServiceModel.Discovery.FindCriteria>tématu.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Vlastnost umožňuje určit koncový bod zjišťování, který se má použít. Obvykle je <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>to, ale může to být libovolný platný koncový bod.  
  
 Při vytváření vazby, která se má použít ke komunikaci se službou, musíte být opatrní, abyste použili stejnou vazbu jako službu. Jediným rozdílem je, že vazba klienta má <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> v horní části zásobníku. Pokud služba používá jednu ze systémových vazeb, vytvořte novou <xref:System.ServiceModel.Channels.CustomBinding> a předejte ji do konstruktoru, který je <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> poskytnutý systémem. Pak můžete přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> voláním `Insert` do <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> vlastnosti.  
  
 Po přidání <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do vazby a její konfiguraci můžete vytvořit instanci třídy klienta WCF, otevřít ji a volat její metody. Následující příklad používá kanál klienta zjišťování k zjištění služby WCF, která implementuje `ICalculator` třídu (používá se v kurzu Začínáme WCF) a volá svou `Add` metodu.  
  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Zabezpečení a kanál klienta zjišťování  
 Při použití kanálu klienta zjišťování jsou zadány dva koncové body. Jeden se používá pro zprávy zjišťování, obvykle <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>a druhý je koncovým bodem aplikace. Při implementaci zabezpečené služby musí být zajištěna péče o zabezpečení obou koncových bodů. Další informace o zabezpečení najdete v tématu [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
