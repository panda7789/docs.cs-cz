---
title: Architektura syndikace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22df793bd5873d6f69c3a2e86e96d4a1cefcff0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="architecture-of-syndication"></a>Architektura syndikace
Rozhraní API syndikace určená k poskytování formátu jazykově neutrální programovací model, který umožňuje syndikovaný obsah má být zapsán k přenosu v různých formátech. Abstraktní datového modelu se skládá z následujících tříd:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy mapovat úzce konstrukce definované specifikací Atom 1.0, i když některé z názvů se liší.  
  
 V [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], informační kanály syndikace jsou modelovat jako jiný typ pro operace služby, jeden kde návratový typ je jedním z odvozené třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Načtení informačního kanálu je modelovaná jako výměně zpráv požadavků a odpovědí. Klient odešle že požadavek na službu a službu odpoví. Zpráva požadavku je nastaven protokol infrastruktury (například nezpracovaná HTTP) a zpráva odpovědi obsahuje datovou část, která se skládá z formátu obecně známý syndikace (RSS 2.0 nebo Atom 1.0). Služby, které implementují těchto výměn zpráv jsou označovány jako syndikace služby.  
  
 Kontrakt služby syndikace obsahuje sadu operací, které vrací instanci třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> třídy. Následující příklad ukazuje deklaraci rozhraní pro službu syndikace.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 Podpora syndikace je postavený na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací Model REST, která definuje <xref:System.ServiceModel.WebHttpBinding> vazby, který se používá ve spojení s <xref:System.ServiceModel.Description.WebHttpBehavior> chcete zpřístupnit informační kanály jako služby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací Model REST, najdete v části [programování přehled modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
>  Specifikace Atom 1.0 umožňuje zadat v některém z jeho datum konstrukce zlomků sekund. Při serializaci a deserializaci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace ignoruje zlomků sekund.  
  
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
  
-   Klíčovou funkcí syndikace protokoly je rozšíření. Atom 1.0 a RSS 2.0 umožňují přidat atributy a elementy pro informační kanály syndikace, které nejsou definovány v specifikacích. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Programovací model syndikace nabízí dva způsoby práce s vlastní atributy a rozšíření: odvozování novou třídu a volného typu přístup. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Rozšiřitelnost syndikace](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled syndikace WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Mapování objektového modelu syndikace WCF na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
