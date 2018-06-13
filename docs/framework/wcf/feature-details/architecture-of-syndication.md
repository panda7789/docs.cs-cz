---
title: Architektura syndikace
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: f0a6b288860c343157f31f74d5a461fad1784e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492808"
---
# <a name="architecture-of-syndication"></a>Architektura syndikace
Rozhraní API syndikace určená k poskytování formátu jazykově neutrální programovací model, který umožňuje syndikovaný obsah má být zapsán k přenosu v různých formátech. Abstraktní datového modelu se skládá z následujících tříd:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy mapovat úzce konstrukce definované specifikací Atom 1.0, i když některé z názvů se liší.  
  
 Ve Windows Communication Foundation (WCF), informační kanály syndikace jsou modelovat jako jiný typ operace služby, jeden kde návratový typ je jedním z odvozené třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Načtení informačního kanálu je modelovaná jako výměně zpráv požadavků a odpovědí. Klient odešle že požadavek na službu a službu odpoví. Zpráva požadavku je nastaven protokol infrastruktury (například nezpracovaná HTTP) a zpráva odpovědi obsahuje datovou část, která se skládá z formátu obecně známý syndikace (RSS 2.0 nebo Atom 1.0). Služby, které implementují těchto výměn zpráv jsou označovány jako syndikace služby.  
  
 Kontrakt služby syndikace obsahuje sadu operací, které vrací instanci třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Následující příklad ukazuje deklaraci rozhraní pro službu syndikace.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Podpora syndikace je nástavbou programovací Model REST WCF definující <xref:System.ServiceModel.WebHttpBinding> vazby, který se používá ve spojení s <xref:System.ServiceModel.Description.WebHttpBehavior> chcete zpřístupnit informační kanály jako služby. Další informace o programovací Model REST WCF najdete v tématu [programování přehled modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Specifikace Atom 1.0 umožňuje zadat v některém z jeho datum konstrukce zlomků sekund. Při serializaci a deserializaci implementace WCF ignoruje zlomků sekund.  
  
## <a name="object-model"></a>Objektový Model  
 Objektový model pro syndikace se skládá ze skupin tříd v následujících tabulkách.  
  
 Formátování třídy:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> instance do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozených tříd do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> instance do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> odvozených tříd do formátu Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> instance formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationFeed> odvozených tříd do formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> instance formátu RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Třídu, která serializuje <xref:System.ServiceModel.Syndication.SyndicationItem> odvozených tříd do formátu RSS 2.0.|  
  
 Třídy modelu objektu:  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Třída zastupující kategorii syndikace informačního kanálu.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Základní třída, která představuje syndikace obsah.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Třída, která představuje příponu syndikace elementu.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Kolekce <xref:System.ServiceModel.Syndication.SyndicationElementExtension> objekty.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Třída, která představuje objekt informačního kanálu nejvyšší úrovně.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Třída zastupující položku informačního kanálu.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Třída, která představuje odkaz v rámci kanálu syndikace nebo položky.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Vytvořit třídu, která představuje s Atom osoby.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Třída, která představuje verze podporovaných syndikace protokolu.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Třída, která představuje všechny <xref:System.ServiceModel.Syndication.SyndicationItem> obsahu, který se má zobrazit pro koncového uživatele.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Výčet představující různého typu obsahu text syndikace podporována.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Třída, která představuje syndikace obsah, který se skládá z adresy URL na jiný prostředek.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Třída, která představuje syndikace obsah, který se zobrazí v prohlížeči.|  
  
 Abstrakce základní data v objektovém modelu jsou informační kanál a položky, které odpovídají <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> třídy. Informační kanál zpřístupní některá metadata úrovni informační kanál (například název, popis a autor), umístění pro uložení neznámá rozšíření a sadu položek, které tvoří zbytek informace obsah informačního kanálu. Položku zpřístupní některá metadata úrovni položek (například název, souhrn a PublicationDate), umístění pro uložení neznámá rozšíření a obsah elementu, který obsahuje zbývající obsah informace položky. Abstrakce základní informační kanál a položky jsou podporovány další třídy, které představují běžné konstrukce dat odkazovaný ve specifikacích Atom 1.0 a RSS.  
  
 Informace v instanci informačního kanálu lze převést na mnoha různých formátech XML. Spravuje proces převodu do a z XML <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Tato třída je abstraktní. konkrétní implementace jsou k dispozici pro Atom 1.0 a RSS 2.0 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Pokud chcete použít odvozené třídy informačního kanálu, použijte buď <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> nebo <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> jako umožňují zadat do odvozené třídy informačního kanálu. Pokud chcete použít položku odvozené třídy, použijte buď <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> nebo <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> jako umožňují zadat odvozené položky třída třetím stranám odvodit, provádění <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pro podporu různých syndikačních formátů.  
  
## <a name="extensibility"></a>Rozšiřitelnost  
  
-   Klíčovou funkcí syndikace protokoly je rozšíření. Atom 1.0 a RSS 2.0 umožňují přidat atributy a elementy pro informační kanály syndikace, které nejsou definovány v specifikacích. Programovací model syndikace WCF nabízí dva způsoby práce s vlastní atributy a rozšíření: odvozování novou třídu a volného typu přístup. Další informace najdete v tématu [rozšiřitelnost syndikace](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Mapování objektového modelu syndikace WCF na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
