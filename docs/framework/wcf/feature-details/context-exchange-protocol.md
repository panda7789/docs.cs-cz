---
title: Protokol kontextové výměny
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 86d2a19b086fbd5d6be6f1a084bfd7aaace0e250
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597433"
---
# <a name="context-exchange-protocol"></a>Protokol kontextové výměny
Tato část popisuje protokol výměny kontextu, představený ve službě Windows Communication Foundation (WCF) verze .NET Framework verze 3,5. Tento protokol umožňuje klientovi klientským kanálem přijmout kontext dodaný službou a použít ho u všech dalších požadavků této služby odesílaných přes stejnou instanci kanálu klienta. Implementace kontextu protokolu Exchange může použít jeden z následujících dvou mechanismů k rozšíření kontextu mezi serverem a klientem: soubory cookie protokolu HTTP nebo hlavičku SOAP.  
  
 Protokol výměny kontextu je implementován ve vrstvě vlastního kanálu. Kanál komunikuje kontext do a z aplikační vrstvy pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> Vlastnosti. Pro přenos mezi koncovými body je hodnota kontextu buď serializována jako hlavička protokolu SOAP na vrstvě kanálu, nebo převedena do nebo z vlastností zprávy, které reprezentují požadavek HTTP a odpověď. V druhém případě je očekáváno, že jedna z podkladových vrstev kanálu převádí vlastnosti zprávy žádosti HTTP a odpovědi na soubory cookie protokolu HTTP v uvedeném pořadí. Volba mechanismu používaného k výměně kontextu se provádí pomocí <xref:System.ServiceModel.Channels.ContextExchangeMechanism> vlastnosti v <xref:System.ServiceModel.Channels.ContextBindingElement> . Platné hodnoty jsou `HttpCookie` nebo `SoapHeader` .  
  
 Na straně klienta může instance kanálu fungovat ve dvou režimech na základě nastavení vlastnosti kanálu <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> .  
  
## <a name="mode-1-channel-context-management"></a>Režim 1: Správa kontextu kanálu  
 Toto je výchozí režim, ve kterém <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastaveno na `true` . V tomto režimu kontextový kanál spravuje kontext a ukládá kontext do mezipaměti během své životnosti. Kontext lze načíst z vlastnosti kanálu prostřednictvím kanálu `IContextManager` voláním `GetContext` metody. Kanál je také možné před otevřením předem inicializovat pomocí konkrétního kontextu voláním `SetContext` metody na vlastnost kanálu. Po inicializaci kanálu s jeho kontextem nelze resetovat.  
  
 Následuje seznam invariant v tomto režimu:  
  
- Jakýkoli pokus o resetování kontextu pomocí `SetContext` po otevření kanálu vyvolá výjimku <xref:System.InvalidOperationException> .  
  
- Jakýkoli pokus o odeslání kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> odchozí zprávy vyvolá výjimku <xref:System.InvalidOperationException> .  
  
- Pokud je přijata zpráva ze serveru s určitým kontextem, pokud již byl kanál inicializován pomocí konkrétního kontextu, výsledkem je <xref:System.ServiceModel.ProtocolException> .  
  
    > [!NOTE]
    > Je vhodné přijmout počáteční kontext ze serveru jenom v případě, že je kanál otevřený bez explicitního nastavení kontextu.  
  
- <xref:System.ServiceModel.Channels.ContextMessageProperty>Příchozí zpráva je vždycky null.  
  
## <a name="mode-2-application-context-management"></a>Režim 2: Správa kontextu aplikace  
 Toto je režim, pokud <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> je nastaven na `false` . V tomto režimu kontextový kanál nespravuje kontext. Je zodpovědností aplikace za účelem získání, správy a použití kontextu pomocí <xref:System.ServiceModel.Channels.ContextMessageProperty> . Jakýkoli pokus o volání `GetContext` nebo `SetContext` výsledky v <xref:System.InvalidOperationException> .  
  
 Bez ohledu na to, v jakém režimu je zvolený objekt pro vytváření kanálů klienta <xref:System.ServiceModel.Channels.IRequestChannel> , podporuje <xref:System.ServiceModel.Channels.IRequestSessionChannel> vzorce pro <xref:System.ServiceModel.Channels.IDuplexSessionChannel> výměnu zpráv, a.  
  
 Ve službě je instance kanálu zodpovědná za převod kontextu dodaného klientem na příchozí zprávy do <xref:System.ServiceModel.Channels.ContextMessageProperty> . K vlastnosti zprávy pak může mít aplikační vrstva nebo jiné kanály dál v zásobníku volání. Kanály služby také umožňují, aby vrstva aplikace určovala novou hodnotu kontextu, která se má rozšířit zpátky do klienta, a to připojením <xref:System.ServiceModel.Channels.ContextMessageProperty> ke zprávě odpovědi. Tato vlastnost je převedena na hlavičku protokolu SOAP nebo soubor cookie protokolu HTTP obsahující kontext, který závisí na konfiguraci vazby. Naslouchací proces kanálu služby podporuje <xref:System.ServiceModel.Channels.IReplyChannel> , <xref:System.ServiceModel.Channels.IReplySessionChannel> a <xref:System.ServiceModel.Channels.IReplySessionChannel> vzory výměny zpráv.  
  
 Protokol výměny kontextu zavádí novou `wsc:Context` hlavičku SOAP, která představuje kontextové informace, když se soubory cookie protokolu HTTP nepoužívají k šíření kontextu. Schéma záhlaví kontextu umožňuje pro libovolný počet podřízených elementů, z nichž každý má řetězcový klíč a obsah řetězce. Následuje příklad záhlaví kontextu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 V `HttpCookie` režimu jsou soubory cookie nastaveny pomocí `SetCookie` hlavičky. Název souboru cookie je `WscContext` . Hodnota souboru cookie je kódování Base64 `wsc:Context` hlavičky. Tato hodnota je uzavřená v uvozovkách.  
  
 Hodnota kontextu musí být během přenosu chráněna před změnou, a to z důvodu ochrany hlaviček protokolu WS-Addressing – záhlaví slouží k určení místa odeslání žádosti do služby. `wsc:Context`Záhlaví je proto nutné digitálně podepsat nebo podepsat a zašifrovat na úrovni protokolu SOAP nebo přenosu, pokud vazba nabízí možnost ochrany zpráv. Pokud jsou soubory cookie protokolu HTTP použity ke rozšiřování kontextu, měly by být chráněny pomocí zabezpečení přenosu.  
  
 Koncové body služby, které vyžadují podporu pro protokol Exchange kontextu, můžou být v publikovaných zásadách explicitní. Byly zavedeny dvě nové kontrolní výrazy zásad, které reprezentují požadavek, aby klient podporoval protokol Exchange kontextu na úrovni protokolu SOAP nebo povolil podporu souborů cookie protokolu HTTP. Generování těchto kontrolních výrazů do zásad služby je řízeno hodnotou <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> vlastnosti následujícím způsobem:  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader> se vygeneruje následující kontrolní výraz:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie> se vygeneruje následující kontrolní výraz:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Průvodce interoperabilitou protokolů webových služeb](web-services-protocols-interoperability-guide.md)
