---
title: Použití kanálu klienta zjišťování
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: 2d9dd68d233541f4d8cb3185adc1023cd5a19de1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184255"
---
# <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování
Při psaní klientské aplikace WCF potřebujete znát adresu koncového bodu služby, kterou voláte. V mnoha situacích není předem známa adresa koncového bodu služby nebo se adresa služby v průběhu času mění. Kanál klienta zjišťování umožňuje napsat klientskou aplikaci WCF, popsat službu, kterou chcete volat, a kanál klienta automaticky odešle požadavek na sondu. Když služba odpoví, kanál klienta zjišťování načte adresu koncového bodu pro službu z odpovědi sondy a použije ji k volání služby.  
  
## <a name="using-the-discovery-client-channel"></a>Použití kanálu klienta zjišťování  
 Chcete-li použít kanál klienta zjišťování, přidejte instanci zásobníku <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> klientských kanálů. Případně můžete použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> a je automaticky přidán do vazby, pokud již není k dispozici.  
  
> [!CAUTION]
> Doporučuje se, <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> že je nejvyšší prvek v zásobníku klientského kanálu. Všechny element vazby, který <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> je přidán nad <xref:System.ServiceModel.ChannelFactory> musí ujistěte se, že nebo `Via` kanál, který `CreateChannel` vytvoří nepoužívá adresu koncového bodu nebo adresu (předána metodě), protože nemusí obsahovat správnou adresu.  
  
 Třída <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> obsahuje dvě veřejné vlastnosti:  
  
1. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, který se používá k popisu služby, kterou chcete volat.  
  
2. <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A>který určuje koncový bod zjišťování, do kterého chcete odesílat zprávy zjišťování.  
  
 Vlastnost <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> umožňuje zadat servisní smlouvu, kterou hledáte, všechny požadované identifikátory URI oboru a maximální počet času při pokusu o otevření kanálu. Typ smlouvy je určen voláním <xref:System.ServiceModel.Discovery.FindCriteria>konstruktoru . Do vlastnosti lze přidat <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> identifikátory URI oboru. Vlastnost <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> umožňuje zadat maximální počet výsledků, ke kterým se klient pokusí připojit. Při přijetí odpovědi sondy se klient pokusí otevřít kanál pomocí adresy koncového bodu z odpovědi sondy. Pokud dojde k výjimce klient přesune na další odpověď sonda a čeká na další odpovědi, které mají být přijaty v případě potřeby. Pokračuje v tom, dokud kanál je úspěšně otevřen nebo maximální počet výsledků je dosaženo. Další informace o těchto <xref:System.ServiceModel.Discovery.FindCriteria>nastaveních naleznete v tématu .  
  
 Vlastnost <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> umožňuje zadat koncový bod zjišťování, který se má použít. Obvykle se <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>jedná o , ale může to být libovolný platný koncový bod.  
  
 Při vytváření vazby pro komunikaci se službou, musíte být opatrní používat přesně stejnou vazbu jako služba. Jediným rozdílem je, že <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> vazba klienta má v horní části zásobníku. Pokud služba používá jednu ze systémem poskytovaných <xref:System.ServiceModel.Channels.CustomBinding> vazeb, vytvořte nové a <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> předat v systému poskytované vazby konstruktoru. Pak můžete přidat <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> voláním `Insert` <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> na vlastnost.  
  
 Jakmile jste přidali <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> do vazby a nakonfigurovali ji, můžete vytvořit instanci třídy wcf klienta, otevřít ji a volat její metody. Následující příklad používá kanál klienta zjišťování ke zjištění služby WCF, která implementuje `ICalculator` třídu `Add` (použitou v kurzu Začínáme wcf) a volá její metodu.  
  
```csharp
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
 Při použití kanálu klienta zjišťování jsou určeny dva koncové body. Jeden se používá pro <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>zjišťování zpráv, obvykle a druhý je koncový bod aplikace. Při implementaci zabezpečené služby je třeba dbát na zabezpečení obou koncových bodů. Další informace o zabezpečení naleznete v tématu [Zabezpečení služeb a klientů](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).
