---
title: Co je to Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5301bf3a2fed35dbdd0046e01eb2acb9083a290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="what-is-windows-communication-foundation"></a>Co je to Windows Communication Foundation
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]je rozhraní pro vytváření aplikací orientovaných na služby. Pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], může odesílat data jako asynchronní zprávy z jedné služby koncového bodu do jiného. Koncový bod služby můžou být součástí nepřetržitě dostupná služba hostované službou IIS, nebo může být služby hostované v aplikaci. Koncový bod může být klient služby, která vyžaduje data z koncového bodu služby. Zprávy může být stejně jednoduché jako jeden znak nebo word odeslán jako XML, nebo jako datový proud binárních dat jako komplexní. Několik ukázkových scénářů patří:  
  
-   Zabezpečené službu ke zpracování obchodní transakce.  
  
-   Služba, která poskytuje aktuální data s jinými uživateli, jako je například provoz sestavy nebo jiné monitorování služby.  
  
-   Konverzace službu, která umožní dvou osob, které umožňují komunikovat nebo vyměňovat data v reálném čase.  
  
-   Řídicí panel aplikace, který posuzuje jednu nebo více služeb pro data a uvede v prezentaci logické.  
  
-   Vystavení pracovního postupu implementovaná pomocí modelu Windows Workflow Foundation jako služby WCF.  
  
-   Informační kanály aplikaci Silverlight pro cyklické dotazování na služby pro nejnovější data.  
  
 Při vytváření takové aplikace bylo možné před existenci [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usnadňuje vývoj koncových bodů než kdy dřív. Souhrnně [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] je určená k poskytování spravovaného přístupu k vytvoření webové služby a klienty webové služby.  
  
## <a name="features-of-wcf"></a>Funkce služby WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]obsahuje následující sadu funkcí. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Orientaci na služby**  
  
     Jedním z důsledků standardy WS je, že [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umožňuje vytvářet *služby zaměřené na konkrétní* aplikace. Architektura orientovaná na služby (SOA) je závislá na webové služby pro odesílat a přijímat data. Služeb mají obecné výhodou se volně vázány místo pevně z jedné aplikace do jiné. Vztah volně vázány znamená, že libovolného klienta vytvořili na jakékoli platformě může připojit k žádné službě tak dlouho, dokud základní kontrakty jsou splněny.  
  
-   **Interoperabilita**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]implementuje moderní oborových standardů interoperability webové služby. [!INCLUDE[crabout](../../../includes/crabout-md.md)]najdete v části Podporované standardy [vzájemná spolupráce a integrace](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Více vzorů zpráv**  
  
     Zprávy se vyměňují v jednom z několika vzory. Nejběžnější vzor je požadavek nebo odpověď vzor, kde jeden koncový bod vyžaduje data z druhého koncového bodu. Druhý odpovědi koncového bodu. Existují další vzory, jako je jednosměrný zpráv, ve kterém jeden koncový bod odešle zprávu bez jakékoli očekávání odpověď. Složitější vzor je vzor duplexní exchange, kde dva koncové body připojení a odesílat data a zpět, podobně jako program pro zasílání rychlých zpráv. [!INCLUDE[crabout](../../../includes/crabout-md.md)]jak implementovat jiná zpráva exchange vzory pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v části [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Metadata služby**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]podporuje publikování metadat služby pomocí formáty zadaný v průmyslové standardy, jako je například WSDL, schématu XML a WS-zásady. Tato metadata lze použít k automatickému generování a konfigurace klientů pro přístup k [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Metadata lze publikovat prostřednictvím protokolu HTTP a HTTPS nebo přes standardní webové služby Metadata Exchange. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Metadata](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Kontrakty dat**  
  
     Protože [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] je sestaven pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], zahrnuje také popisný kód metody poskytnutí kontrakty chcete vynutit. Jeden z typů universal smluv je kontrakt dat. V podstatě jak používáte kódové vaši službu pomocí Visual C# nebo Visual Basic, nejjednodušší způsob, jak zpracovávat data je vytvořením tříd, které představují data entity s vlastnostmi, které patří do dat entity. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]obsahuje komplexní systém pro práci s daty tímto způsobem snadno. Po vytvoření třídy, které představují data služby automaticky vytvoří metadata, která umožňuje klientům v souladu se datové typy, které jste vytvořili. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Použití kontraktů dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Zabezpečení**  
  
     Zprávy se můžou šifrovat k ochraně osobních údajů a může vyžadovat uživatelům ověřit dříve, než mohou přijímat zprávy. Zabezpečení se dají implementovat pomocí známých standardy, jako je protokol SSL nebo WS-SecureConversation. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Zabezpečení](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Více přenosy a kódování**  
  
     Na žádném z několik předdefinovaných přenosové protokoly a kódování nelze odesílat zprávy. Nejvíce běžné protokol kódování a je k odeslání zprávy protokolu SOAP text kódovaný pomocí je protokolu HTTP (HyperText Transfer) pro použití na Internetu. Alternativně [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umožňuje odesílání zpráv přes protokol TCP, pojmenované kanály nebo služby MSMQ. Tyto zprávy mohou být kódovaný jako text nebo pomocí optimalizované binární formát.  Binární data můžete efektivně pomocí standardní MTOM odeslat. Pokud zadaný přenosy ani kódování podle potřeby můžete vytvořit vlastní vlastní přenos nebo kódování. [!INCLUDE[crabout](../../../includes/crabout-md.md)]přenosy a nepodporuje kódování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v části [přenosy](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Spolehlivé a zařazených do fronty zpráv**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]podporuje systém exchange spolehlivé zpráv pomocí spolehlivé relace implementuje přes WS-spolehlivé zasílání zpráv a pomocí služby MSMQ. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Podpora spolehlivé a zařazených do fronty zasílání zpráv v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v části [fronty a spolehlivé relace](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Trvanlivý zprávy**  
  
     Trvanlivý zpráva je ten, který se nikdy ztraceno v důsledku přerušení v komunikaci. Zprávy ve tvaru trvanlivý zpráva se vždy uloží do databáze. Pokud dojde k narušení služeb, databáze můžete obnovit výměny zpráv, když se obnoví připojení. Můžete také vytvořit trvanlivý zprávu pomocí [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Služeb pracovních postupů](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **Transakce**  
  
     WCF také podporuje transakce pomocí jedné z tři modely transakcí: WS-AtomicTtransactions, rozhraní API v <xref:System.Transactions> obor názvů a Microsoft Distributed Transaction Coordinator. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Podpora transakcí v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] najdete v části [transakce](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **Rozhraní AJAX a podpora REST**  
  
     REST je příkladem měnící technologie Web 2.0. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]může být nakonfigurován pro zpracování "prostý" data XML, který není uzavřen do obálky protokolu SOAP. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Můžete také rozšířit pro zajištění podpory konkrétní formáty XML, například ATOM (oblíbených RSS standard) a i bez XML formátů, jako je například JSON JavaScript Object Notation ().  
  
-   **Rozšíření**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Architektura má počet bodů rozšiřitelnosti. Pokud je potřeba další funkce, je počet vstupních bodů, které umožňují přizpůsobit chování služby. [!INCLUDE[crabout](../../../includes/crabout-md.md)]body rozšiřitelnosti k dispozici, najdete v části [rozšíření WCF](../../../docs/framework/wcf/extending/extending-wcf.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF integrace s jinými technologiemi společnosti Microsoft  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]je flexibilní platforma. Z důvodu tuto flexibilitu potřebují extrémně [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] se také používá v několika dalších produktů společnosti Microsoft. Porozuměním Základy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], máte okamžitě využívat, pokud používáte některý z těchto produktů.  
  
 První technologie spárovat s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] byl Windows Workflow Foundation (WF). Pracovní postupy zjednodušují vývoj aplikací zapouzdřením kroky v pracovním postupu jako "aktivity". V první verzi [!INCLUDE[wf2](../../../includes/wf2-md.md)], vývojář museli vytvořit hostitele pro pracovní postup. Další verzi [!INCLUDE[wf2](../../../includes/wf2-md.md)] byla integrována [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Který povolen žádný pracovní postup snadno hostitelem [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby; to provedete tak, že automaticky zvolíte WF/WCF typu projektu v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 také využívá [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] technologií komunikace. BizTalk je určena pro příjem a transformovat data z jednoho standardizované formátu do druhého. Zprávy musí doručit do jeho centrální se zprávou, kde zprávu lze je transformovat pomocí striktní mapování, nebo pomocí jedné z BizTalk funkce jako je například modul jeho pracovních postupů. Teď můžete použít BizTalk [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] adaptér obchodnímu systému (LOB) pro doručení zprávy do pole zpráva.  
  
 Microsoft Silverlight je platforma pro vytváření webových aplikací umožňuje vzájemnou spolupráci, bohaté, které umožňují vývojářům vytvářet weby náročných na média (třeba streamování videa). Od verze 2, Silverlight doplnil [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] komunikace technologií pro připojení aplikacím Silverlight [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] koncové body.  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] Aplikační server je vytvořené speciálně pro nasazení a správě aplikací, které používají [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pro komunikaci. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] Obsahuje bohatou nástrojů a konfigurační možnosti speciálně pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]– aplikace s podporou služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel>  
 [Základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Architektura Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)  
 [Pokyny a osvědčené postupy](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Průvodce dokumentací](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Ukázky Windows Communication Foundation](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
