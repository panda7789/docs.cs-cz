---
title: Protokol kontextové výměny
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 00adb68d96f77ce0953811d13b5377ec4ed1e0ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185268"
---
# <a name="context-exchange-protocol"></a>Protokol kontextové výměny
Tato část popisuje protokol pro výměnu kontextu zavedený ve verzi WCF (Windows Communication Foundation) .NET Framework verze 3.5. Tento protokol umožňuje kanálu klienta přijmout kontext dodaný službou a použít jej na všechny následné požadavky na tuto službu odeslanou prostřednictvím stejné instance kanálu klienta. Implementace protokolu kontextové výměny může použít jeden z následujících dvou mechanismů k šíření kontextu mezi serverem a klientem: http cookies nebo hlavička SOAP.  
  
 Protokol výměny kontextu je implementován ve vlastní vrstvě kanálu. Kanál komunikuje kontext do a z aplikační <xref:System.ServiceModel.Channels.ContextMessageProperty> vrstvy pomocí vlastnosti. Pro přenos mezi koncovými body je hodnota kontextu serializována jako hlavička SOAP ve vrstvě kanálu nebo převedena na nebo z vlastností zprávy, které představují požadavek a odpověď HTTP. V druhém případě se očekává, že jeden z vrstev základní kanál převede http požadavek a odpověď zprávy vlastnosti a z http cookies, resp. Volba mechanismu s použitím mechanismu použitého k <xref:System.ServiceModel.Channels.ContextExchangeMechanism> výměně <xref:System.ServiceModel.Channels.ContextBindingElement>kontextu se provádí pomocí vlastnosti na . Platné hodnoty `HttpCookie` `SoapHeader`jsou nebo .  
  
 Na straně klienta může instance kanálu pracovat ve dvou režimech založených <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>na nastavení vlastnosti kanálu .  
  
## <a name="mode-1-channel-context-management"></a>Režim 1: Správa kontextu kanálu  
 Toto je výchozí <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> režim, `true`ve kterém je nastavena na . V tomto režimu kontextový kanál spravuje kontext a ukládá kontext během jeho životnosti. Kontext lze načíst z kanálu `IContextManager` prostřednictvím `GetContext` vlastnosti kanálu voláním metody. Kanál lze také předem inicializovat s určitým kontextem před otevřením voláním `SetContext` metody na vlastnosti kanálu. Jakmile je kanál inicializován s kontextem, nelze jej obnovit.  
  
 Následuje seznam invariants v tomto režimu:  
  
- Jakýkoli pokus o obnovení `SetContext` kontextu pomocí po otevření <xref:System.InvalidOperationException>kanálu vyvolá .  
  
- Jakýkoli pokus o odeslání <xref:System.ServiceModel.Channels.ContextMessageProperty> kontextu pomocí v odchozí <xref:System.InvalidOperationException>zprávy vyvolá .  
  
- Pokud je zpráva přijata ze serveru s určitým kontextem, pokud kanál již byl <xref:System.ServiceModel.ProtocolException>inicializován s určitým kontextem, výsledkem je .  
  
    > [!NOTE]
    > Je vhodné přijímat počáteční kontext ze serveru pouze v případě, že kanál je otevřen bez jakéhokoli kontextu explicitně.  
  
- Příchozí <xref:System.ServiceModel.Channels.ContextMessageProperty> zpráva je vždy null.  
  
## <a name="mode-2-application-context-management"></a>Režim 2: Správa kontextu aplikace  
 Toto je <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> režim, `false`kdy je nastavena na . V tomto režimu kontextový kanál nespravuje kontext. Je odpovědností aplikace načíst, spravovat a použít kontext <xref:System.ServiceModel.Channels.ContextMessageProperty>pomocí . Jakýkoli pokus `GetContext` o `SetContext` volání <xref:System.InvalidOperationException>nebo výsledkem v .  
  
 Bez ohledu na to, který <xref:System.ServiceModel.Channels.IRequestChannel>režim <xref:System.ServiceModel.Channels.IRequestSessionChannel>je <xref:System.ServiceModel.Channels.IDuplexSessionChannel> vybrán, podporuje toto způsoby obnovení klientského kanálu , a vzory výměny zpráv.  
  
 Ve službě je instance kanálu zodpovědná za převod kontextu poskytnutého klientem na <xref:System.ServiceModel.Channels.ContextMessageProperty>příchozí zprávy na . Vlastnost zprávy pak lze přistupovat aplikační vrstvy nebo jiné kanály dále v zásobníku volání. Kanály služeb také umožňují aplikační vrstvě určit novou hodnotu kontextu, která má <xref:System.ServiceModel.Channels.ContextMessageProperty> být rozšířena zpět klientovi, připojením a ke zprávě odpovědi. Tato vlastnost je převedena na hlavičku SOAP nebo soubor cookie HTTP, který obsahuje kontext, který závisí na konfiguraci vazby. Naslouchací <xref:System.ServiceModel.Channels.IReplySessionChannel>proces <xref:System.ServiceModel.Channels.IReplySessionChannel> kanálu služby podporuje <xref:System.ServiceModel.Channels.IReplyChannel>vzory , a výměnu zpráv.  
  
 Protokol výměny kontextu zavádí `wsc:Context` novou hlavičku SOAP představující kontextové informace, pokud se soubory cookie PROTOKOLU HTTP nepoužívají k šíření kontextu. Schéma záhlaví kontextu umožňuje libovolný počet podřízených prvků, každý s řetězcovou klávesou a obsahem řetězce. Následuje příklad záhlaví kontextu.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 V `HttpCookie` režimu jsou soubory `SetCookie` cookie nastaveny pomocí záhlaví. Název souboru `WscContext`cookie je . Hodnota souboru cookie je base64 kódování `wsc:Context` záhlaví. Tato hodnota je uzavřena v uvozovkách.  
  
 Hodnota kontextu musí být chráněna před změnami při přenosu ze stejného důvodu ws adresování hlavičky jsou chráněny – záhlaví slouží k určení, kam odeslat požadavek na službu. Záhlaví `wsc:Context` je proto nutné digitálně podepsána nebo podepsána a šifrována na úrovni SOAP nebo přenosu, pokud vazba nabízí možnost ochrany zpráv. Při použití souborů cookie HTTP k šíření kontextu by měly být chráněny pomocí zabezpečení přenosu.  
  
 Koncové body služby, které vyžadují podporu pro protokol výměny kontextu můžete explicitní v publikované zásady. Dvě nová tvrzení zásad byly zavedeny představují požadavek pro klienta na podporu protokolu výměny kontextu na úrovni SOAP nebo povolit podporu souborů cookie HTTP. Generování těchto tvrzení do zásad y služby je řízeno hodnotou vlastnosti <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> následujícím způsobem:  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, je generován následující kontrolní výraz:  
  
    ```xml  
    <IncludeContext
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Pro <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, je generován následující kontrolní výraz:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Viz také

- [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
