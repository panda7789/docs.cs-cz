---
title: Architektura syndikace
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: 718778993a953ae819a2bee5a4a050a81d3a4b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587518"
---
# <a name="architecture-of-syndication"></a>Architektura syndikace
Syndikace rozhraní API je navrženo tak, aby poskytovalo formátově neutrální programovací model, který umožňuje zápis do sítě v nejrůznějších formátech. Abstraktní datový model se skládá z následujících tříd:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy jsou úzce mapovány na konstrukce definované ve specifikaci Atom 1,0, i když se některé názvy liší.  
  
 V Windows Communication Foundation (WCF) se informační kanály syndikace modelují jako jiné operace typu služby, jedna, kde je návratový typ jednou z odvozených tříd <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . Načtení informačního kanálu je modelováno jako výměna zpráv o odezvě požadavků. Klient odešle požadavek službě a služba odpoví. Zpráva požadavku se nastavuje přes protokol infrastruktury (například RAW HTTP) a zpráva s odpovědí obsahuje datovou část, která se skládá z běžně srozumitelného formátu syndikace (RSS 2,0 nebo Atom 1,0). Služby, které implementují tyto výměny zpráv, se nazývají syndikacé služby.  
  
 Kontrakt služby syndikace se skládá ze sady operací, které vrací instanci <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Následující příklad ukazuje deklaraci rozhraní pro službu syndikace.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Podpora syndikace je postavená na programovacím modelu WCF REST, který definuje <xref:System.ServiceModel.WebHttpBinding> vazbu, která se používá ve spojení s nástrojem k zpřístupnění <xref:System.ServiceModel.Description.WebHttpBehavior> kanálů jako služeb. Další informace o programovacím modelu služby WCF REST naleznete v tématu [Přehled programovacího modelu webového HTTP WCF](wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
> Specifikace Atom 1,0 umožňuje určení zlomků sekund, které mají být zadány v libovolném z jeho konstrukcí data. Při serializaci a deserializaci implementace WCF ignoruje zlomky sekund.  
  
## <a name="object-model"></a>Objektový model  
 Objektový model pro syndikaci se skládá ze skupin tříd v následujících tabulkách.  
  
 Třídy formátování:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationFeed> instance do formátu Atom 1,0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozené třídy ve formátu Atom 1,0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationItem> instance do formátu Atom 1,0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationItem> odvozené třídy ve formátu Atom 1,0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationFeed> instance do formátu RSS 2,0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozené třídy do formátu RSS 2,0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationItem> instance do formátu RSS 2,0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Třída, která serializace <xref:System.ServiceModel.Syndication.SyndicationItem> odvozené třídy do formátu RSS 2,0.|  
  
 Třídy objektového modelu:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Třída, která představuje kategorii syndikačního informačního kanálu.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Základní třída, která představuje obsah syndikace.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Třída, která představuje rozšíření syndikačního elementu.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Kolekce objektů <xref:System.ServiceModel.Syndication.SyndicationElementExtension>.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Třída, která představuje objekt informačního kanálu nejvyšší úrovně.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Třída, která představuje položku informačního kanálu.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Třída, která představuje odkaz v rámci syndikačního informačního kanálu nebo položky.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Třída, která představuje konstrukci osoby Atom.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Třída, která představuje podporované verze protokolu syndikace.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Třída, která představuje libovolný obsah, který se <xref:System.ServiceModel.Syndication.SyndicationItem> zobrazí koncovému uživateli.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Výčet, který představuje různé typy obsahu syndikace textu.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Třída, která představuje obsah syndikace, který se skládá z adresy URL jiného prostředku.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Třída, která představuje obsah syndikace, který není zobrazen v prohlížeči.|  
  
 Základní abstrakce dat v objektovém modelu jsou informační kanál a položka, které odpovídají <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> třídám a. Informační kanál zpřístupňuje některá metadata na úrovni informačního kanálu (například název, popis a autor), umístění pro ukládání neznámých rozšíření a sadu položek, které tvoří zbytek obsahu informačního kanálu. Položka zpřístupňuje některá metadata na úrovni položky (například title, Summary a PublicationDate), umístění pro uložení neznámých rozšíření a element obsahu, který obsahuje zbytek obsahu informace o položce. Základní abstrakce kanálu a položky jsou podporovány dalšími třídami, které představují běžné datové konstrukce, na které odkazuje specifikace Atom 1,0 a RSS.  
  
 Informace přenesené do instance informačního kanálu lze převést na nejrůznější formáty XML. Proces převodu do a z XML je spravován <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídou. Tato třída je abstraktní; konkrétní implementace jsou k dispozici pro Atom 1,0 a RSS 2,0 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> . Chcete-li použít odvozené třídy informačního kanálu, použijte buď <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> nebo, <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> protože umožňují zadat odvozenou třídu informačního kanálu. Chcete-li použít odvozené třídy položek, použijte buď <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> nebo <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> , protože umožňují určit odvozenou třídu položky třetí strany mohou odvodit svou vlastní implementaci <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pro podporu různých formátů syndikace.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
  
- Klíčovou funkcí Syndikačních protokolů je rozšiřitelnost. Atom 1,0 i RSS 2,0 umožňují přidat atributy a prvky do kanálů syndikace, které nejsou definovány ve specifikacích. Model programování Syndikace WCF nabízí dva způsoby práce s vlastními atributy a rozšířeními: Odvození nové třídy a volně typovaného přístupu. Další informace najdete v tématu [rozšiřitelnost syndikace](syndication-extensibility.md).  
  
## <a name="see-also"></a>Viz také

- [Syndikace WCF – přehled](wcf-syndication-overview.md)
- [Mapování modelu objektu syndikace WCF na Atom a RSS](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
