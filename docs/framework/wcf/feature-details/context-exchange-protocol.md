---
title: Protokol kontextové výměny
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: a6bc0ac45282d94a6aea8dbbdb5a7d34163c692e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217000"
---
# <a name="context-exchange-protocol"></a>Protokol kontextové výměny
Tato část popisuje protokol kontextové výměny zavedená ve Windows Communication Foundation (WCF) verzi rozhraní .NET Framework verze 3.5. Tento protokol umožňuje kanálu klienta přijímat kontext získáte ho od služby a použít ji k této službě odesílá přes stejnou instanci kanálu klienta také všechny následné požadavky. Implementace protokol kontextové výměny můžete použít jednu z následujících dvou mechanismů rozšíření kontextu mezi serverem a klientem: Soubory cookie protokolu HTTP nebo záhlaví SOAP.  
  
 Protokol kontextové výměny je implementována ve vlastním kanálu vrstvě. Kanál komunikuje kontextu do a z aplikace pomocí vrstvy <xref:System.ServiceModel.Channels.ContextMessageProperty> vlastnost. Hodnota kontextu pro přenos mezi koncovými body, je buď serializován jako záhlaví SOAP ve vrstvě kanálu nebo převést na nebo z vlastnosti zprávy, které představují požadavků HTTP a odpovědí. V takovém případě se očekává, že jeden z kanálu vrstvách převede vlastnosti zprávy požadavku a odpovědi HTTP do a z soubory cookie protokolu HTTP, v uvedeném pořadí. Volba mechanismus, který se používá k výměně kontextu se provádí pomocí <xref:System.ServiceModel.Channels.ContextExchangeMechanism> vlastnost <xref:System.ServiceModel.Channels.ContextBindingElement>. Platné hodnoty jsou `HttpCookie` nebo `SoapHeader`.  
  
 Na straně klienta, můžete instanci kanálu pracovat ve dvou režimech na základě nastavení na vlastnosti kanálu <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Režim 1: Správu kontextu kanálu  
 Toto je výchozí režim kde <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastavena na `true`. V tomto režimu kanálu kontextu spravuje kontextu a ukládá do mezipaměti kontextu během celé jeho životnosti. Kontext můžete získat z kanálu prostřednictvím vlastnosti kanálu `IContextManager` voláním `GetContext` metody. Kanál může být také předem inicializovaných s konkrétní kontext před voláním otevření `SetContext` metodu na vlastnosti kanálu. Jakmile kanál je inicializován s kontextem nelze obnovit.  
  
 Následuje seznam výstupních podmínek v tomto režimu:  
  
-   Žádný pokus o resetování kontextu pomocí `SetContext` po otevřené vyvolá kanál <xref:System.InvalidOperationException>.  
  
-   Žádný pokus o odeslání kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> v odchozí zprávě vyvolá <xref:System.InvalidOperationException>.  
  
-   Pokud je přijata zpráva ze serveru s konkrétní kontext, když kanál již byl inicializován s konkrétní kontext, výsledkem je <xref:System.ServiceModel.ProtocolException>.  
  
    > [!NOTE]
    >  Je vhodné počáteční kontextu přijetí ze serveru, pouze v případě, že otevření kanálu bez kontextu explicitně nastaven.  
  
-   <xref:System.ServiceModel.Channels.ContextMessageProperty> Na příchozí zpráva má vždy hodnotu null.  
  
## <a name="mode-2-application-context-management"></a>Režim 2: Správa kontextu aplikací  
 Jedná se o režim při <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastavena na `false`. V tomto režimu nespravuje kanálu kontextu kontextu. Je zodpovědností aplikace načíst, spravovat a zavedení kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty>. Žádný pokus o volání `GetContext` nebo `SetContext` vede <xref:System.InvalidOperationException>.  
  
 Bez ohledu na to režimu, který je vybrán objekt pro vytváření kanálů klienta podporuje <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, a <xref:System.ServiceModel.Channels.IDuplexSessionChannel> zpráv exchange vzory.  
  
 Ve službě, je zodpovědný za převod kontextu dodaný klientem na příchozích zprávách na instanci kanálu <xref:System.ServiceModel.Channels.ContextMessageProperty>. Vlastnost zprávy lze přistupovat pomocí aplikačního nebo jiných kanálů další nahoru v zásobníku volání. Kanály služby umožňují aplikační vrstvu můžete zadat novou hodnotu kontextu mohly rozšířit zpět do klienta připojením <xref:System.ServiceModel.Channels.ContextMessageProperty> zprávu s odpovědí. Tato vlastnost je převedena na záhlaví SOAP nebo souboru cookie HTTP, který obsahuje kontext, který závisí na konfiguraci vazby. Tato služba podporuje naslouchacího procesu kanálu <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>, a <xref:System.ServiceModel.Channels.IReplySessionChannel> zpráv exchange vzory.  
  
 Protokol kontextové výměny zavádí nový `wsc:Context` záhlaví SOAP k reprezentaci informace o kontextu při šíření kontextu nejsou používány soubory cookie protokolu HTTP. Schéma hlavičky kontextu umožňuje pro libovolný počet podřízených prvků, každý s klíčem řetězce a obsah řetězce. Následuje příklad hlavičku kontextu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Když v `HttpCookie` režimu, soubory cookie jsou nastaveny pomocí `SetCookie` záhlaví. Název souboru cookie je `WscContext`. Hodnota souboru cookie, který je Base64 kódování `wsc:Context` záhlaví. Tato hodnota je uzavřena v uvozovkách.  
  
 Hodnota kontextu musí být chráněné před změnami při přenosu ze stejného důvodu jsou chráněny záhlaví WS-Addressing – záhlaví se používá k určení, kam chcete odeslat žádost o služby. `wsc:Context` Záhlaví je proto potřeba digitálně podepsaný nebo podepsat a zašifrovat na úrovni protokolu SOAP nebo přenos při vazbě nabízí možnosti ochrany zprávy. V případě šíření kontextu používají soubory cookie protokolu HTTP, by měl být chráněn pomocí zabezpečení přenosu.  
  
 Koncové body služby, které vyžadují podporu pro protokol kontextové výměny může být definován v publikované zásady. Dvě nové kontrolní výrazy zásad byly zavedeny představující požadavku pro klienta podporovat protokol kontextové výměny na úrovni protokolu SOAP nebo povolit podporu souborů cookie protokolu HTTP. Generování těchto kontrolních výrazů do zásad služby se řídí hodnotou <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> vlastnost následujícím způsobem:  
  
-   Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, je vygenerována následující výraz:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
-   Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, je vygenerována následující výraz:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
