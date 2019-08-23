---
title: Protokol kontextové výměny
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 19780cccc74f8c3615dc844e47be7613ca5f8bc1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911207"
---
# <a name="context-exchange-protocol"></a>Protokol kontextové výměny
Tato část popisuje protokol výměny kontextu, představený ve službě Windows Communication Foundation (WCF) verze .NET Framework verze 3,5. Tento protokol umožňuje klientovi klientským kanálem přijmout kontext dodaný službou a použít ho u všech dalších požadavků této služby odesílaných přes stejnou instanci kanálu klienta. Implementace kontextu protokolu Exchange může použít jeden z následujících dvou mechanismů k rozšíření kontextu mezi serverem a klientem: Soubory cookie protokolu HTTP nebo hlavička protokolu SOAP.  
  
 Protokol výměny kontextu je implementován ve vrstvě vlastního kanálu. Kanál komunikuje kontext do a z aplikační vrstvy pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> vlastnosti. Pro přenos mezi koncovými body je hodnota kontextu buď serializována jako hlavička protokolu SOAP na vrstvě kanálu, nebo převedena do nebo z vlastností zprávy, které reprezentují požadavek HTTP a odpověď. V druhém případě je očekáváno, že jedna z podkladových vrstev kanálu převádí vlastnosti zprávy žádosti HTTP a odpovědi na soubory cookie protokolu HTTP v uvedeném pořadí. Volba mechanismu používaného k výměně kontextu se provádí pomocí <xref:System.ServiceModel.Channels.ContextExchangeMechanism> vlastnosti <xref:System.ServiceModel.Channels.ContextBindingElement>v. Platné hodnoty jsou `HttpCookie` nebo `SoapHeader`.  
  
 Na straně klienta může instance kanálu fungovat ve dvou režimech na základě nastavení vlastnosti <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>kanálu.  
  
## <a name="mode-1-channel-context-management"></a>Režim 1: Správa kontextu kanálu  
 Toto je výchozí režim, ve <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> kterém je nastaveno `true`na. V tomto režimu kontextový kanál spravuje kontext a ukládá kontext do mezipaměti během své životnosti. Kontext lze načíst z vlastnosti `IContextManager` kanálu prostřednictvím kanálu `GetContext` voláním metody. Kanál je také možné před otevřením předem inicializovat pomocí konkrétního kontextu voláním `SetContext` metody na vlastnost kanálu. Po inicializaci kanálu s jeho kontextem nelze resetovat.  
  
 Následuje seznam invariant v tomto režimu:  
  
- Jakýkoli pokus o resetování kontextu pomocí `SetContext` po otevření kanálu <xref:System.InvalidOperationException>vyvolá výjimku.  
  
- Jakýkoli pokus o odeslání kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> odchozí zprávy <xref:System.InvalidOperationException>vyvolá výjimku.  
  
- Pokud je přijata zpráva ze serveru s určitým kontextem, pokud již byl kanál inicializován pomocí konkrétního kontextu, výsledkem <xref:System.ServiceModel.ProtocolException>je.  
  
    > [!NOTE]
    > Je vhodné přijmout počáteční kontext ze serveru jenom v případě, že je kanál otevřený bez explicitního nastavení kontextu.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty> Příchozí zpráva je vždycky null.  
  
## <a name="mode-2-application-context-management"></a>Režim 2: Správa kontextu aplikace  
 Toto je režim, pokud <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastaven na `false`. V tomto režimu kontextový kanál nespravuje kontext. Je zodpovědností aplikace za účelem získání, správy a použití kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty>. Jakýkoli pokus o volání `GetContext` nebo `SetContext` výsledky v <xref:System.InvalidOperationException>.  
  
 Bez ohledu na to, v jakém režimu je zvolený objekt pro <xref:System.ServiceModel.Channels.IDuplexSessionChannel> vytváření kanálů klienta, podporuje <xref:System.ServiceModel.Channels.IRequestChannel>vzorce pro výměnu zpráv, <xref:System.ServiceModel.Channels.IRequestSessionChannel>a.  
  
 Ve službě je instance kanálu zodpovědná za převod kontextu dodaného klientem na příchozí zprávy do <xref:System.ServiceModel.Channels.ContextMessageProperty>. K vlastnosti zprávy pak může mít aplikační vrstva nebo jiné kanály dál v zásobníku volání. Kanály služby také umožňují, aby vrstva aplikace určovala novou hodnotu kontextu, která se má rozšířit zpátky do klienta, a to připojením <xref:System.ServiceModel.Channels.ContextMessageProperty> ke zprávě odpovědi. Tato vlastnost je převedena na hlavičku protokolu SOAP nebo soubor cookie protokolu HTTP obsahující kontext, který závisí na konfiguraci vazby. Naslouchací proces kanálu služby podporuje <xref:System.ServiceModel.Channels.IReplyChannel>, <xref:System.ServiceModel.Channels.IReplySessionChannel>a <xref:System.ServiceModel.Channels.IReplySessionChannel> vzory výměny zpráv.  
  
 Protokol výměny kontextu zavádí novou `wsc:Context` hlavičku SOAP, která představuje kontextové informace, když se soubory cookie protokolu HTTP nepoužívají k šíření kontextu. Schéma záhlaví kontextu umožňuje pro libovolný počet podřízených elementů, z nichž každý má řetězcový klíč a obsah řetězce. Následuje příklad záhlaví kontextu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 V `HttpCookie` režimu jsou soubory cookie nastaveny `SetCookie` pomocí hlavičky. Název souboru cookie je `WscContext`. Hodnota souboru cookie je kódování `wsc:Context` Base64 hlavičky. Tato hodnota je uzavřená v uvozovkách.  
  
 Hodnota kontextu musí být během přenosu chráněna před změnou, a to z důvodu ochrany hlaviček protokolu WS-Addressing – záhlaví slouží k určení místa odeslání žádosti do služby. `wsc:Context` Záhlaví je proto nutné digitálně podepsat nebo podepsat a zašifrovat na úrovni protokolu SOAP nebo přenosu, pokud vazba nabízí možnost ochrany zpráv. Pokud jsou soubory cookie protokolu HTTP použity ke rozšiřování kontextu, měly by být chráněny pomocí zabezpečení přenosu.  
  
 Koncové body služby, které vyžadují podporu pro protokol Exchange kontextu, můžou být v publikovaných zásadách explicitní. Byly zavedeny dvě nové kontrolní výrazy zásad, které reprezentují požadavek, aby klient podporoval protokol Exchange kontextu na úrovni protokolu SOAP nebo povolil podporu souborů cookie protokolu HTTP. Generování těchto kontrolních výrazů do zásad služby je řízeno hodnotou <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> vlastnosti následujícím způsobem:  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>se vygeneruje následující kontrolní výraz:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>se vygeneruje následující kontrolní výraz:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
