---
title: "Přehled modelu kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f6f45b788d825fed3c8f5d627190dd8911ec4c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="channel-model-overview"></a>Přehled modelu kanálu
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Zásobník kanál je vrstveného komunikačního balíku s jeden nebo více kanálů, které zpracovávají zprávy. V dolní části zásobníku je přenos kanálu, který je zodpovědný za přizpůsobení zásobníku kanál pro základní přenos (například TCP, HTTP, SMTP a dalších typů přenosu.). Kanály poskytují nízké úrovně programovací model pro odesílání a přijímání zpráv. Tento programovací model závisí na několika rozhraní a dalších typů souhrnně označované jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model kanálu. Toto téma popisuje tvarů kanál, vytváření základní kanál naslouchání služby (service) a kanálu (na straně klienta).  
  
## <a name="channel-stack"></a>Kanál zásobníku  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Koncové body komunikovat s world pomocí komunikačního balíku volat zásobník kanálu. Následující diagram porovná zásobník kanál s další komunikace zásobníky, například protokol TCP/IP.  
  
 ![Model kanálu](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 První, podobnost: V obou případech každý vrstvy v zásobníku poskytuje některé abstrakce na světě níže, který vrstvy a že abstrakce pouze na vrstvu nad ním viditelné. Jednotlivé úrovně používá abstrakce pouze vrstvě přímo pod ním. Také v obou případech, pokud dva zásobníky komunikují, jednotlivé úrovně komunikuje s odpovídající vrstvy v zásobníku jiné, například vrstvy IP komunikuje s vrstvy IP a vrstvě TCP TCP vrstvy a tak dále.  
  
 Nyní, rozdíly: zásobník při protokolu TCP byla navržená k poskytování abstrakci fyzické síti, zásobník kanál určená k poskytování abstrakci nejen jak zprávy je doručen, to znamená, přenos, ale také další funkce, například to, co se v zpráva nebo co protokolu se používá pro komunikaci, včetně přenosu ale mnohem víc než. Například prvku vazby spolehlivé relace je součástí zásobníku kanál, ale není pod přenos nebo přenos sám sebe. Tato abstrakce je dosaženo tím, že kanál dolní v zásobníku přizpůsobit podkladový přenosový protokol k architektuře zásobníku kanál a potom spoléhat na další kanály až v zásobníku a zajistit tak komunikaci funkce jako je například spolehlivosti záruky a zabezpečení.  
  
 Zprávy toku prostřednictvím komunikačního balíku jako <xref:System.ServiceModel.Channels.Message> objekty. Jak ukazuje předchozí obrázek, kanál dolní nazývá kanál přenosu. Je kanál, který je zodpovědný za odesílání a příjmu zprávy do od jiných výrobců. To zahrnuje je zodpovědností transformace <xref:System.ServiceModel.Channels.Message> objekt do a z formátu používaný ke komunikaci s ostatními stranami. Výše kanál přenosu může existovat libovolný počet kanály protokolů se každý odpovědné za poskytování komunikace funkce jako je například spolehlivé zárukami. Kanály protokolů pracovat zpráv předávaných mezi je ve formě <xref:System.ServiceModel.Channels.Message> objektu. Se obvykle buď transformace zprávy, například přidání hlavičky nebo šifruje obsah, nebo odesílat a přijímat zprávy ovládacího prvku vlastní protokol, například přijetí potvrzování.  
  
## <a name="channel-shapes"></a>Kanál tvarů  
 Každý kanál implementuje jedno nebo více rozhraní, které jsou známé jako rozhraní tvar kanálu nebo kanálu tvarů. Kanál tvarů poskytují metody orientované na komunikaci, jako odesílání a příjem nebo požadavku a odpovědi, implementuje kanál a uživatel kanálu volání. Na bázi tvarů kanál je <xref:System.ServiceModel.Channels.IChannel> rozhraní, což je rozhraní, které poskytuje `GetProperty` \<T > metoda určena jako vrstvený mechanismus pro přístup k libovolné funkce vystavené kanály v zásobníku. Pět kanálu tvarů, které rozšiřují <xref:System.ServiceModel.Channels.IChannel> jsou:  
  
-   <xref:System.ServiceModel.Channels.IInputChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplyChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Dále, každý z těchto tvarů má ekvivalentní, který rozšiřuje <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> pro podporu relací. Jsou to:  
  
-   <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kanál tvarů jsou uspořádány po některé základní zprávy exchange vzory nepodporuje existující přenosové protokoly. Například jednosměrný zasílání zpráv odpovídá <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> pár, odpovídá požadavku a odpovědi <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> páry a obousměrný duplexní komunikace odpovídá <xref:System.ServiceModel.Channels.IDuplexChannel> (který rozšiřuje obě <xref:System.ServiceModel.Channels.IInputChannel> a <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programování s kanál zásobníku  
 Zásobníky kanál jsou obvykle vytvoří pomocí vzoru objekt pro vytváření, kde vytvoří vazbu kanálu zásobníku. Na straně odesílání vazbu slouží k vytvoření <xref:System.ServiceModel.ChannelFactory>, která zase zásobníku sestavení a kanál a vrátí odkaz na horní kanálu v zásobníku. Aplikace pak může pomocí tohoto kanálu odesílat zprávy. Další informace najdete v tématu [programování na úrovni kanálu klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Na straně příjmu vazbu slouží k vytvoření <xref:System.ServiceModel.Channels.IChannelListener>, která naslouchá pro příchozí zprávy. <xref:System.ServiceModel.Channels.IChannelListener> Poskytuje zprávy do aplikace naslouchá vytvořením zásobníky kanál a blokováním odkaz na aplikaci nejvyšší kanálu. Aplikace se pak používá tento kanál pro příjem příchozích zpráv. Další informace najdete v tématu [programování na úrovni služby kanálů](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Objektový Model kanálu  
 Objektový model kanálu je základní sada rozhraní potřebnou k implementaci kanály, kanál naslouchací procesy a objekty factory kanálu. Existují také některé základní třídy zadané v vlastních implementací pomoct.  
  
 Kanál moduly pro naslouchání jsou zodpovědní za naslouchání pro příchozí zprávy, pak je doručování vrstvu nad prostřednictvím kanálů vytvořen naslouchací proces kanálu nástroje.  
  
 Objekty Factory kanál jsou zodpovědní za vytváření kanály, které se používají pro odesílání zpráv a pro zavření všech kanálů vytvářely při zavření kanálu.  
  
 <xref:System.ServiceModel.ICommunicationObject>je základní rozhraní, které určuje základní stav počítače, ve kterém implementace všechny objekty komunikace. <xref:System.ServiceModel.Channels.CommunicationObject>poskytuje implementaci pro tento základní rozhraní, které mohou ostatní třídy kanál odvozovat z místo znovu implementace rozhraní. Ale to není potřeba: můžete implementovat vlastní kanál <xref:System.ServiceModel.ICommunicationObject> přímo a není dědí <xref:System.ServiceModel.Channels.CommunicationObject>. Žádné třídy na obrázku 3 jsou považovány za součást model kanálu; jsou k dispozici pro implementátory vlastní kanál, kteří chtějí vytvořit kanály pomocné rutiny.  
  
 ![Model kanálu](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Následující témata popisují objektový model kanál, jakož i různých oblastí vývoj, které pomáhají vytvářet vlastní kanály.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Služba: Naslouchací objekty kanálů a kanály](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Popisuje posluchači kanál naslouchání pro příchozí kanály v aplikaci služby.|  
|[Klient: Objekty pro vytváření kanálů a kanály](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Popisuje továren kanál vytvořit kanály pro připojení k aplikaci služby.|  
|[Principy změn stavů](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Popisuje, jak <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> rozhraní modelů změny stavu v kanály.|  
|[Výběr vzoru výměny zpráv](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Popisuje šest vzory exchange základní zpráv, které může podporovat kanály.|  
|[Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Popisuje způsob zpracování chyb a výjimek ve vlastní kanály.|  
|[Konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Popisuje postup podporují použití vlastní kanály z modelu aplikace a pro export a import metadat pomocí vazby a prvky vazeb.|
