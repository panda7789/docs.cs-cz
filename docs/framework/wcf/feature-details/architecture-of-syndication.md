---
title: Architektura syndikace
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: 4083f7f7ef3fc986e9a7c430b8ed8cfe451c9d86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075909"
---
# <a name="architecture-of-syndication"></a>Architektura syndikace
Rozhraní API syndikace je navržené pro poskytování formátu neutrální programovací model, který umožňuje syndikovaný obsah má být proveden zápis k přenosu v různých formátech. Abstraktní datový model obsahuje následující třídy:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy mapování úzce konstrukce definované ve specifikaci Atom 1.0, i když některé názvy se liší.  
  
 Ve Windows Communication Foundation (WCF), informační kanály syndikace jsou modelovány jako jiný druh operace služby, jeden ve kterém návratový typ je jedním z odvozené třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Načítání informačního kanálu je modelovaná jako výměně zpráv žádost odpověď. Klient odešle že požadavek na službu a službu reaguje. Zprávy s požadavkem je nastavena protokolu infrastruktury (třeba nezpracovaná HTTP) a zprávy s odpovědí obsahuje datovou část, která se skládá z formátu běžně používané syndikace (RSS 2.0 nebo Atom 1.0). Služby, které implementují tyto výměny zpráv se označují jako služby syndikace.  
  
 Kontrakt služby syndikace sestává ze sady operací, které vrací instanci <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Následující příklad ukazuje deklaraci rozhraní pro služby syndikace.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Syndikace podpory je nástavbou programovacího modelu WCF REST, která definuje <xref:System.ServiceModel.WebHttpBinding> vazby, který se používá ve spojení s <xref:System.ServiceModel.Description.WebHttpBehavior> zpřístupnit informačních kanálů jako služby. Další informace o programovacího modelu WCF REST, naleznete v tématu [WCF Web HTTP programovací Model Overview](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Desetinné části sekund zadaná v některém z jeho datum konstrukce umožňuje specifikaci Atom 1.0. Při serializaci a deserializaci implementace WCF ignoruje zlomků sekund.  
  
## <a name="object-model"></a>Objektový Model  
 Objektový model pro syndikaci se skládá ze skupin tříd v následujících tabulkách.  
  
 Formátování třídy:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> instance do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozené třídy pro formát Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> instance do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> odvozené třídy pro formát Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> instance do formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozené třídy formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> instance do formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Třída, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> odvozené třídy formátu RSS 2.0.|  
  
 Objekt třídy modelu:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Třída zastupující kategorii informačního kanálu syndikace.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Základní třída, která představuje syndikace obsahu.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Třída, která představuje rozšíření elementu syndikace.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Kolekce <xref:System.ServiceModel.Syndication.SyndicationElementExtension> objekty.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Třída, která představuje objekt informačního kanálu nejvyšší úrovně.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Třída, která představuje položku informačního kanálu.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Třída, která představuje odkaz v rámci informačního kanálu syndikace nebo položku.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Vytvoření třídy reprezentující Atom osoby.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Třída zastupující verze protokolu podporované syndikace.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Třídu, která představuje jakékoli <xref:System.ServiceModel.Syndication.SyndicationItem> obsahu, který se má zobrazit pro koncového uživatele.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Výčet, který představuje různé druhy textu syndikace obsahu nepodporuje.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Třída zastupující syndikace obsahu, který se skládá z adresy URL na jiný prostředek.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Třída zastupující syndikace obsahu, který se zobrazí v prohlížeči.|  
  
 Abstrakce základní data v objektovém modelu jsou informační kanál a položky, které odpovídají <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> třídy. Informační kanál poskytuje některé metadat na úrovni kanálu (třeba název, popis a autor), umístění pro uložení neznámá rozšíření a sadu položek, které tvoří zbývající obsah informace informačního kanálu. Položka zpřístupní některých metadat na úrovni položek (například Title, Summary a PublicationDate), umístění pro uložení neznámá rozšíření a obsah elementu, který obsahuje zbývající informace obsahu položky. Abstrakce základní kanál a položka podporuje další třídy, které představují běžné konstrukce data odkazuje ve specifikacích Atom 1.0 a RSS.  
  
 Informace v instanci informačního kanálu lze převést na širokou škálu formátů XML. Spravuje proces převodu do a ze souboru XML <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Tato třída je abstraktní. konkrétní implementace jsou k dispozici pro Atom 1.0 a RSS 2.0 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Odvozené třídy informačního kanálu, použijte buď <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> nebo <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> jako umožňují zadat odvozené třídy informačního kanálu. Pokud chcete použít položky odvozené třídy, použijte buď <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> nebo <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> jako umožňují zadat položky odvozené třídy třetích stran lze odvodit vlastní implementaci <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pro podporu různých syndikačních formátů.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
  
-   Klíčovou funkcí služby syndikace protokolů je rozšíření. Atom 1.0 i RSS 2.0 umožňují přidat atributy a elementy pro informační kanály syndikace, které nejsou definované specifikací. Programovací model syndikace WCF nabízí dva způsoby práce s vlastní atributy a rozšíření: odvození nové třídy a volného typu přístup. Další informace najdete v tématu [rozšiřitelnost syndikace](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Viz také:

- [Syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Mapování modelu objektu syndikace WCF na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
