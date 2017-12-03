---
title: "Použití kanálu klienta zjišťování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f012cc43d7160b737e5a9a5d4ceb5e50e91d07a1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování
Při zápisu klientské aplikace WCF je třeba vědět adresa koncového bodu služby, ke kterému se připojujete. V mnoha situacích adresa koncového bodu služby není známa předem nebo adresu služby změny v čase. Kanálem klienta zjišťování umožňuje psát aplikace klienta WCF, popisují službu, kterou chcete volat a kanálem klienta automaticky odešle žádost o test. Jakmile služba odpoví, kanálem klienta zjišťování načte adresa koncového bodu služby z testu odpovědi a použije k vyvolání služby.  
  
## <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování  
 K použití kanálu klienta zjišťování, přidá instanci <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do zásobníku kanálu klienta. Případně můžete použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> se automaticky přidá do vašeho vazby Pokud již nejsou přítomny.  
  
> [!CAUTION]
>  Dále je doporučeno <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je nejvyšší element v zásobníku kanál vašeho klienta. Libovolný element vazby, který se přidá na <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> musí Ujistěte se, že <xref:System.ServiceModel.ChannelFactory> nebo kanál vytvoří nepoužívá adresa koncového bodu nebo `Via` adresu (předaný `CreateChannel` metoda) protože nemusí obsahovat správný Adresa.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> Třída obsahuje dvě veřejné vlastnosti:  
  
1.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, který se používá k popisu služby, který chcete použít.  
  
2.  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>Určuje, který koncový bod zjišťování k odesílání zprávy zjišťování.  
  
 <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> Vlastnost umožňuje určit kontrakt služby, který hledáte, potřebné obor identifikátory URI a maximální počet času, který se pokusí otevřít kanál. Typ smlouvy je zadána při volání konstruktoru <xref:System.ServiceModel.Discovery.FindCriteria>. Identifikátory URI oboru lze přidat do <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> vlastnost. <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> Vlastnost umožňuje určit maximální počet výsledků, na které se klient pokusí připojit k. Při obdržení odpovědi testu klient se pokusí otevřít kanál pomocí adresa koncového bodu z testu odpovědi. Pokud dojde k výjimce klient přesune další kontroly odpovědi, čekání na další odpovědi k přijetí v případě potřeby. Uděláte to tak dlouho, dokud úspěšně otevření kanálu nebo je dosaženo maximálního počtu výsledků pokračuje. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tato nastavení najdete v části <xref:System.ServiceModel.Discovery.FindCriteria>.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> Vlastnost umožňuje určit koncový bod zjišťování používat. Obvykle je to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, ale může být libovolný platný koncový bod.  
  
 Při vytváření vazby ke komunikaci se službou, musí být přesně stejnou vazbu použít jako služba. Jediným rozdílem je, že má klient vazby <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> v horní části zásobníku. Pokud služba používá jedna z vazeb poskytovaných systémem, vytvořte novou <xref:System.ServiceModel.Channels.CustomBinding> a předat vazby poskytované systémem <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> konstruktor. Potom můžete přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> voláním `Insert` na <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> vlastnost.  
  
 Po přidání <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> k vaší vazby a nakonfiguruje ji, můžete vytvořit instanci třídy klienta WCF, otevřete ho a volat její metody. Následující příklad používá ke zjišťování služby WCF, který implementuje kanálem klienta zjišťování `ICalculator` – třída (používá se v tomto kurzu získávání spuštění WCF) a volání jeho `Add` metoda.  
  
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
  
## <a name="security-and-the-discovery-client-channel"></a>Zabezpečení a kanálem klienta zjišťování  
 Pokud používáte kanálem klienta zjišťování, jsou specifikované dva koncové body. Jeden se obvykle používá pro zjišťování zprávy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, a druhá je koncový bod aplikace. Při implementaci zabezpečení služby, musí dát pozor na zabezpečené oba koncové body. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zabezpečení, najdete v části [zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
