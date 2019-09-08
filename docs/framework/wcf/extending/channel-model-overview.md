---
title: Přehled modelu kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 362a7392d9dbaedb1942280a6c3b6c8f2139afe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795886"
---
# <a name="channel-model-overview"></a>Přehled modelu kanálu
Zásobník kanálů Windows Communication Foundation (WCF) je Vícevrstvá komunikační sada s jedním nebo více kanály, které zpracovávají zprávy. V dolní části zásobníku je transportní kanál zodpovědný za přizpůsobení zásobníku kanálu k základnímu přenosu (například TCP, HTTP, SMTP a dalších typů přenosů). Kanály poskytují model programování nízké úrovně pro odesílání a příjem zpráv. Tento programovací model spoléhá na několik rozhraní a dalších typů, které jsou souhrnně označovány jako model kanálu WCF. Toto téma popisuje obrazce kanálů, konstrukci základního naslouchacího procesu kanálu (u služby) a továrny kanálů (na klientovi).  
  
## <a name="channel-stack"></a>Zásobník kanálů  
 Koncové body WCF komunikují s World pomocí komunikačního zásobníku označovaného jako zásobník kanálů. Následující diagram porovnává zásobník kanálů s jinými komunikačními zásobníky, například TCP/IP.  
  
 ![Channel Model](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Nejprve podobnosti: V obou případech jsou v každé vrstvě zásobníku k dispozici některé abstrakce světa pod touto vrstvou a zpřístupnění této abstrakce pouze vrstvě přímo nad ní. Každá vrstva používá abstrakci pouze vrstvy přímo pod ní. V obou případech také při komunikaci dvou zásobníků komunikuje každá vrstva s odpovídající vrstvou v druhém zásobníku, například vrstva IP komunikuje s vrstvou IP adresy a vrstvou TCP s vrstvou TCP atd.  
  
 Teď rozdíly: I když byl zásobník TCP navržený tak, aby poskytoval abstrakci fyzické sítě, zásobník kanálů je navržený tak, aby poskytoval abstrakci nejen toho, jak je zpráva doručena, to znamená přenos, ale i další funkce, jako je například zpráva, co je ve zprávě. protokol se používá ke komunikaci, včetně přenosu, ale mnohem víc. Například element s vazbou spolehlivé relace je součástí zásobníku kanálů, ale není pod přenosem nebo samotným přenosem. Tato abstrakce se dosahuje tím, že vyžaduje spodní kanál v zásobníku, aby se přizpůsobila architektura zásobníku kanálu a pak se spoléhá na další kanály v zásobníku, aby se poskytovaly komunikační funkce, jako je třeba spolehlivost. záruky a zabezpečení.  
  
 Zprávy proudí prostřednictvím komunikačního zásobníku <xref:System.ServiceModel.Channels.Message> jako objekty. Jak je znázorněno na obrázku výše, Spodní kanál se nazývá transportní kanál. Je to kanál, který zodpovídá za odesílání a příjem zpráv z jiných stran. To zahrnuje zodpovědnost <xref:System.ServiceModel.Channels.Message> proti transformaci objektu do formátu používaného ke komunikaci s ostatními stranami a z něj. Nad transportním kanálem může být každý z nich zodpovědný libovolný počet kanálů protokolu, jako je například spolehlivý záruka na doručení. Kanály protokolu fungují na zprávy, které je procházejí v podobě <xref:System.ServiceModel.Channels.Message> objektu. Obvykle buď transformují zprávu, například přidáním záhlaví nebo šifrováním těla, nebo odesílají a přijímají vlastní zprávy řídicího protokolu, například potvrzení o doručení.  
  
## <a name="channel-shapes"></a>Obrazce kanálu  
 Každý kanál implementuje jedno nebo více rozhraní označovaných jako rozhraní obrazce kanálu nebo obrazce kanálů. Tyto obrazce kanálů poskytují metody zaměřené na komunikaci, jako je například odeslání a přijetí nebo vyžádání a odpověď na to, že kanál implementuje a uživatel volání kanálu. Na základu obrazců kanálu je <xref:System.ServiceModel.Channels.IChannel> rozhraní, což je rozhraní, které `GetProperty` \<poskytuje metodu T >, která je určená jako vrstvený mechanismus pro přístup k libovolným funkcím vystaveným kanály v zásobníku. Pět obrazců kanálu, které rozšiřuje <xref:System.ServiceModel.Channels.IChannel> :  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Každý z těchto tvarů má navíc ekvivalent, který rozšiřuje <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> na relace podpory. Toto jsou:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 Obrazce kanálu jsou vzorované po některých základních vzorech výměny zpráv podporovaných existujícími transportními protokoly. Například jednosměrné zasílání zpráv <xref:System.ServiceModel.Channels.IInputChannel> odpovídá <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IDuplexChannel> páru, požadavek-odpověď odpovídá dvojicímaobousměrněduplexníkomunikaciodpovídá<xref:System.ServiceModel.Channels.IReplyChannel> / (která rozšiřuje obě <xref:System.ServiceModel.Channels.IInputChannel> <xref:System.ServiceModel.Channels.IOutputChannel>i).  
  
## <a name="programming-with-the-channel-stack"></a>Programování se zásobníkem kanálů  
 Zásobníky kanálů se většinou vytvářejí pomocí modelu továrny, ve kterém vazba vytváří zásobník kanálů. Na straně odeslání je použita vazba k sestavení a <xref:System.ServiceModel.ChannelFactory>, který zase sestaví zásobník kanálu a vrátí odkaz na horní kanál v zásobníku. Aplikace pak může tento kanál použít k posílání zpráv. Další informace najdete v tématu [programování na úrovni kanálu klienta](client-channel-level-programming.md).  
  
 Na straně příjmu se používá vazba k sestavení <xref:System.ServiceModel.Channels.IChannelListener>a, která naslouchá příchozím zprávám. <xref:System.ServiceModel.Channels.IChannelListener> Poskytuje zprávy pro naslouchající aplikace vytvořením zásobníků kanálů a předáním odkazu na aplikaci do nejvyššího kanálu. Aplikace pak použije tento kanál pro příjem příchozích zpráv. Další informace najdete v tématu [programování na úrovni kanálu služby](service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>Objektový model kanálu  
 Objektový model kanálu je základní sada rozhraní vyžadovaných k implementaci kanálů, naslouchací procesy kanálu a objekty pro vytváření kanálů. K dispozici jsou také některé základní třídy, které pomáhají při vlastních implementacích.  
  
 Naslouchací procesy kanálu jsou zodpovědné za naslouchání příchozích zpráv a jejich doručování do vrstvy výše přes kanály vytvořené naslouchacím kanálem kanálu.  
  
 Továrny kanálů jsou zodpovědné za vytváření kanálů používaných pro posílání zpráv a pro zavření všech kanálů, které vytvořily, když je objekt factory kanálu uzavřený.  
  
 <xref:System.ServiceModel.ICommunicationObject>je základní rozhraní, které definuje základní Stavový počítač, který implementují všechny objekty komunikace. <xref:System.ServiceModel.Channels.CommunicationObject>poskytuje implementaci tohoto základního rozhraní, které mohou jiné třídy kanálů odvodit z spíše než opakované implementace rozhraní. To ale není povinné: vlastní kanál může implementovat <xref:System.ServiceModel.ICommunicationObject> přímo a Nedědit z. <xref:System.ServiceModel.Channels.CommunicationObject> Žádná z tříd na obrázku 3 není považována za součást modelu kanálu; jsou pomocníky k dispozici pro vlastní implementátory kanálů, kteří chtějí vytvářet kanály.  
  
 ![Model kanálu](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Následující témata popisují model objektu kanálu a také různé vývojové oblasti, které vám pomůžou vytvářet vlastní kanály.  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Službám Naslouchací procesy kanálu a kanály](service-channel-listeners-and-channels.md)|Popisuje naslouchací procesy kanálu, které naslouchají příchozím kanálům v aplikaci služby.|  
|[Služba Továrny kanálů a kanály](client-channel-factories-and-channels.md)|Popisuje továrny kanálů, které vytvářejí kanály pro připojení k aplikaci služby.|  
|[Principy změn stavů](understanding-state-changes.md)|Popisuje, jak <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> se stav modelů rozhraní mění v kanálech.|  
|[Výběr vzoru výměny zpráv](choosing-a-message-exchange-pattern.md)|Popisuje šest základních vzorů výměny zpráv, které kanály můžou podporovat.|  
|[Zpracování výjimek a chyb](handling-exceptions-and-faults.md)|Popisuje způsob zpracování chyb a výjimek ve vlastních kanálech.|  
|[Konfigurace a podpora metadat](configuration-and-metadata-support.md)|Popisuje, jak podporovat použití vlastních kanálů z modelu aplikace a jak exportovat a importovat metadata pomocí vazeb a elementů vazby.|
