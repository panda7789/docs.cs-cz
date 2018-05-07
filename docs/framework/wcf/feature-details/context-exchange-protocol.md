---
title: Protokol kontextové výměny
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a682b94b1ab659515e618e79230d94f57f140717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="context-exchange-protocol"></a>Protokol kontextové výměny
Tato část popisuje protokol kontextové výměny uvedený ve Windows Communication Foundation (WCF) verzi rozhraní .NET Framework verze 3.5. Tento protokol umožňuje kanálem klienta přijmout kontextu poskytl služby a použijte ho pro všechny následné žádosti do této služby, odešlou přes stejnou instanci kanálu klienta. Implementace protokol kontextové výměny můžete použít jednu z následujících dvou mechanismů rozšíření kontextu mezi serverem a klientem: soubory cookie protokolu HTTP nebo hlavičku protokolu SOAP.  
  
 Protokol kontextové výměny je implementována ve vlastním kanálu vrstvě. Kanál komunikuje kontext do a z aplikace pomocí vrstvy <xref:System.ServiceModel.Channels.ContextMessageProperty> vlastnost. Hodnota kontextu pro přenos mezi koncovými body, je buď serializovanou jako hlavičku protokolu SOAP ve vrstvě kanálu nebo převést na nebo z vlastnosti zprávy, které představují požadavku HTTP a odpovědí. V takovém případě se očekává, že jeden z základní vrstvy kanálu převádí vlastnosti zprávy požadavku a odpovědi HTTP z soubory cookie HTTP, v uvedeném pořadí. Volba používáno k výměně kontextu se provádí pomocí <xref:System.ServiceModel.Channels.ContextExchangeMechanism> vlastnost <xref:System.ServiceModel.Channels.ContextBindingElement>. Platné hodnoty jsou `HttpCookie` nebo `SoapHeader`.  
  
 Na straně klienta mohou instanci kanál pracovat ve dvou režimech na základě nastavení na vlastnost kanál <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Režim 1: Správa kontextu kanál  
 Toto je výchozí režim kde <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastaven na `true`. V tomto režimu kanálu kontextu spravuje kontextu a ukládá do mezipaměti kontextu během celé jeho životnosti. Kontext se dá načíst z tohoto kanálu prostřednictvím vlastnosti kanálu `IContextManager` voláním `GetContext` metoda. Kanál může být také předem inicializovaný s konkrétní kontext před otevíráte voláním `SetContext` metodu vlastnosti kanálu. Po inicializaci kanálu s kontextem nelze obnovit.  
  
 Následuje seznam výstupních podmínek v tomto režimu:  
  
-   Žádný pokus o resetování kontextu pomocí `SetContext` po otevřenou vyvolá kanál <xref:System.InvalidOperationException>.  
  
-   Jakýkoli pokus o odeslání kontext pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> v odchozí zprávy vyvolá <xref:System.InvalidOperationException>.  
  
-   Pokud je přijata zpráva ze serveru s konkrétní kontext, když kanál již byl inicializován s konkrétní kontext, výsledkem <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Je vhodné přijmout počáteční kontext ze serveru pouze v případě, že otevření kanálu bez kontextu explicitně nastaven.  
  
-   <xref:System.ServiceModel.Channels.ContextMessageProperty> Na příchozí zprávy je vždy hodnotu null.  
  
## <a name="mode-2-application-context-management"></a>Režim 2: Správa kontextu aplikací  
 Toto je režim při <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastaven na `false`. V tomto režimu kanálu kontextu nespravuje kontextu. Je zodpovědností aplikace načíst, spravovat a použít kontext pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty>. Jakýkoli pokus o volání `GetContext` nebo `SetContext` vede <xref:System.InvalidOperationException>.  
  
 Bez ohledu na to, ve kterém režimu je zvolen kanálu klienta podporuje <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> zprávy vzory exchange.  
  
 Ve službě, je zodpovědná za převod kontext dodaný klientem na příchozí zprávy do instance kanálu <xref:System.ServiceModel.Channels.ContextMessageProperty>. Vlastnosti zprávy lze přistupovat pomocí aplikační vrstvu nebo jinými kanály další nahoru v zásobníku volání. Kanály služby také povolit aplikační vrstvy zadat novou hodnotu kontextu mohly rozšířit zpět do klienta připojením <xref:System.ServiceModel.Channels.ContextMessageProperty> zprávu s odpovědí. Tato vlastnost je převést hlavičky SOAP nebo souboru cookie HTTP, který obsahuje kontext, který závisí na konfiguraci vazby. Tato služba podporuje kanál naslouchání <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, a <xref:System.ServiceModel.Channels.IReplySessionChannel> zprávy vzory exchange.  
  
 Protokol kontextové výměny představuje novou `wsc:Context` hlavičky SOAP pro reprezentaci informace o kontextu, když HTTP soubory cookie nepoužívají rozšíření kontextu. Schéma záhlaví kontext umožňuje pro libovolný počet podřízených elementů, každý s klíči řetězce a obsah řetězce. Následuje příklad hlavičky kontextu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Když v `HttpCookie` režimu, soubory cookie jsou nastavené pomocí `SetCookie` záhlaví. Název souboru cookie je `WscContext`. Hodnota souboru cookie, který je Base64, pomocí kódování `wsc:Context` záhlaví. Tato hodnota je uzavřena v uvozovkách.  
  
 Hodnota kontextu musí být chráněný proti úpravy při přenosu ze stejného důvodu jsou chráněné WS-Addressing hlavičky – hlavička se používá k určení, kam chcete odeslat žádost o služby. `wsc:Context` Záhlaví je proto potřeba digitálně podepsaný nebo podepsat a zašifrovat na úrovni protokolu SOAP nebo přenos při vazby nabízí možnost ochrany zprávy. Pokud soubory cookie protokolu HTTP se používá k šíření kontextu, by měl být chráněn pomocí zabezpečení přenosu.  
  
 Koncové body služby, které vyžadují podporu pro protokol kontextové výměny může být explicitní v publikované zásad. Dva nové výrazy zásad byly zavedeny představují požadavek pro klienta pro podporu protokol kontextové výměny na úrovni protokolu SOAP nebo povolení souborů cookie podpory protokolu HTTP. Generování těchto kontrolních výrazů do zásady ve službě se řídí hodnota <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> vlastnost následujícím způsobem:  
  
-   Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, je generována následující kontrolní výraz:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, je generována následující kontrolní výraz:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
