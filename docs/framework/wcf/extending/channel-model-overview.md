---
title: Přehled modelu kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 13fe07d1521832ed12ba5770e0bd069ff9b917d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043575"
---
# <a name="channel-model-overview"></a>Přehled modelu kanálu
Zásobník kanál Windows Communication Foundation (WCF) je vrstvený komunikačního balíku pomocí jednoho nebo několika kanálů, které zpracovávají zprávy. V dolní části zásobníku je přenosový kanál, který je zodpovědný za přizpůsobení zásobníku kanálu k přenosu. (například TCP, HTTP, SMTP a jiné typy přenosu.). Kanály nabízejí nižší úrovně programovací model pro odesílání a příjem zpráv. Tento model programování spoléhá na několik rozhraní a další typy souhrnně označované jako model kanálu WCF. Toto téma popisuje kanál tvary, konstrukce základní kanál naslouchání (služba) a objekt pro vytváření kanálů (na straně klienta).  
  
## <a name="channel-stack"></a>Kanál zásobníku  
 Koncových bodů WCF komunikovat na světě pomocí komunikačního balíku volá zásobníku kanálu. Následující diagram porovnává zásobníku kanál pomocí jiných komunikační balíky, například protokol TCP/IP.  
  
 ![Channel Model](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 První, podobnost: Každá vrstva zásobníku v obou případech poskytuje některé abstrakce světa níže, vrstvy a zveřejnění této abstrakční pouze do vrstvy nad ním. Každá vrstva využívá abstrakční vrstvu přímo pod něj. Také v obou případech platí, pokud dva balíčky komunikují, každá vrstva komunikuje s odpovídající vrstvy do zásobníku, například vrstvy IP komunikuje s vrstvou IP a vrstvě protokolu TCP vrstvě protokolu TCP a tak dále.  
  
 Nyní rozdíly: Zatímco protokolů TCP je navržená k poskytování abstrakce fyzickou sítí, kanál zásobníku je navržené pro poskytování abstrakce nejen jak zpráva se doručí, to znamená, přenos, ale také další funkce, jako jsou Novinky ve zprávě, nebo co protokol se používá pro komunikaci, včetně přenosu ale mnohem větší než největší. Například element vazby stabilní relace je součástí zásobníku kanálu, ale není pod přenos nebo přenosu samotného. Tato abstrakce zajišťuje vyžadováním dolní kanálu v zásobníku přizpůsobit podkladový přenosový protokol k architektuře zásobníku kanálu a spoléhání se na další kanály nahoru v zásobníku a zajistit tak komunikaci funkce, jako je spolehlivost zabezpečení a záruky.  
  
 Messages – flow na stránkách komunikačního balíku jako <xref:System.ServiceModel.Channels.Message> objekty. Jak je znázorněno na obrázku výše, je volána v dolní části kanálu přenosový kanál. Je kanál, který je zodpovědný za odesílání a přijímání zpráv do a z jiných stran. Jedná se o odpovědnosti transformace <xref:System.ServiceModel.Channels.Message> objektů do a z formátu používaný ke komunikaci s ostatními stranami. Nad přenosový kanál může existovat libovolný počet kanály protokolů každý odpovídají za poskytování komunikace funkci, jako je například spolehlivé doručování záruky. Kanály protokolů provádět zpráv předávaných mezi nimi ve formě <xref:System.ServiceModel.Channels.Message> objektu. Jsou obvykle buď transformaci zprávy, například přidání hlavičky nebo šifrování těla, nebo odesílat a přijímat zprávy ovládacího prvku vlastní protokol, například na příjem potvrzení.  
  
## <a name="channel-shapes"></a>Kanál obrazce  
 Každý kanál implementuje jedno nebo více rozhraní, které jsou známé jako rozhraní tvar kanál nebo kanál obrazce. Tyto obrazce kanál poskytují metody orientované na komunikaci, jako posílají a přijímají nebo požadavku a odpovědi, že implementuje kanál a kanálu volání. Základní tvary kanálu je <xref:System.ServiceModel.Channels.IChannel> rozhraní, což je rozhraní, které poskytuje `GetProperty` \<T > metoda určené jako vrstvené mechanismus pro přístup k libovolné funkce vystavené kanály v zásobníku. Pěti kanálu tvary, které rozšiřují <xref:System.ServiceModel.Channels.IChannel> jsou:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Dále, každý z těchto tvarů má ekvivalentní, která rozšiřuje <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> pro podporu relace. Toto jsou:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Kanál tvary jsou uspořádány po některé základní zprávy exchange vzory, podporuje stávající přenosové protokoly. Například jednosměrného zasílání zpráv odpovídá <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> pár, odpovídá požadavku a odpovědi <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> páry a obousměrný duplexní komunikaci odpovídá <xref:System.ServiceModel.Channels.IDuplexChannel> (který rozšiřuje oba <xref:System.ServiceModel.Channels.IInputChannel> a <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programování s zásobníku kanálu  
 Zásobníky kanálu se obvykle vytvářejí pomocí vzoru pro objekt pro vytváření, kde vytvoří vazbu kanálu zásobníku. Na straně odesílání vazbu sloužící k sestavení <xref:System.ServiceModel.ChannelFactory>, která zase sestavení kanálu zásobníku a vrátí odkaz na horní části kanálu v zásobníku. Aplikace pak můžete použít tento kanál pro odesílání zpráv. Další informace najdete v tématu [programování na úrovni kanálu klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 Na straně příjmu vazbu sloužící k sestavení <xref:System.ServiceModel.Channels.IChannelListener>, který poslouchá příchozí zprávy. <xref:System.ServiceModel.Channels.IChannelListener> Poskytuje vytvořením kanálu zásobníky a odkazu na aplikaci na hlavní kanál zpracování zpráv do přijímající aplikace. Aplikace pak pomocí tohoto kanálu pro příjem příchozí zprávy. Další informace najdete v tématu [programování na úrovni kanálu služby](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Objektový Model kanálu  
 Objektový model kanálu je základní sadu rozhraní potřebnou k implementaci kanály, moduly pro naslouchání kanálů a objekty pro vytváření kanálů. Existují také některé základní třídy zadané pomáhat při vlastní implementaci.  
  
 Moduly pro naslouchání kanálů zodpovídají za naslouchání pro příchozí zprávy a potom je doručit do vrstvy nad prostřednictvím kanálů vytvořen naslouchací proces kanálu.  
  
 Objekty pro vytváření kanálů zodpovídají za vytváření kanálů, které se používají pro zasílání zpráv a pro zavření všech kanálů vytvořili při zavření objekt pro vytváření kanálů.  
  
 <xref:System.ServiceModel.ICommunicationObject> je rozhraní jádra definující základní stav stavového stroje, které implementují všechny objekty komunikace. <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje implementaci tohoto rozhraní core, který další kanálu třídy lze odvodit z místo znovu implementovat rozhraní. Ale to není potřeba: můžete implementovat vlastní kanál <xref:System.ServiceModel.ICommunicationObject> přímo a není odvozena od <xref:System.ServiceModel.Channels.CommunicationObject>. Žádné třídy na obrázku 3 je považována za součást modelu kanálu jsou k dispozici pro implementátory vlastní kanál, kteří chtějí vytvářet kanály pomocné rutiny.  
  
 ![Channel model](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Toto téma popisuje objektový model kanálu, jakož i různé oblasti rozvoje, které vám pomůžou vytvářet vlastní kanály.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Služba: Moduly pro naslouchání kanálů a kanály](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Popisuje moduly pro naslouchání kanálů, které naslouchají příchozí kanály v aplikaci služby.|  
|[Klient: Objekty pro vytváření kanálů a kanály](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Popisuje vytváření kanálů, které vytvářejí kanály pro připojení k aplikaci služby.|  
|[Principy změn stavů](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Popisuje, jak <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> rozhraní modely změny stavu v kanálech.|  
|[Výběr vzoru výměny zpráv](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Popisuje šest vzory exchange základní zprávy, které může podporovat kanály.|  
|[Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Popisuje způsob zpracování chyb a výjimek do vlastních kanálů.|  
|[Konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Popisuje, jak podporovat používání vlastních kanálů z modelu aplikace a export a import metadat pomocí vazby a prvky vazeb.|
