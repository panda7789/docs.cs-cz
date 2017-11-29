---
title: "Rozšiřitelnost syndikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 13c89b38021f4935044ca439c7dab3837d620caf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="syndication-extensibility"></a>Rozšiřitelnost syndikace
Rozhraní API syndikace určená k poskytování formátu jazykově neutrální programovací model, který umožňuje syndikovaný obsah k zápisu do sítě v různých formátech. Abstraktní datového modelu se skládá z následujících tříd:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy mapovat úzce konstrukce definované specifikací Atom 1.0, i když některé z názvů se liší.  
  
 Klíčovou funkcí syndikace protokoly je rozšíření. Atom 1.0 a RSS 2.0, přidejte do informační kanály syndikace, které nejsou definovány v specifikacích atributy a elementy. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Programovací model syndikace nabízí tyto způsoby práce s vlastní atributy a rozšíření, volného typu přístup a odvozování novou třídu.  
  
## <a name="loosely-typed-access"></a>Přístup volného typu  
 Přidání rozšíření odvozením novou třídu vyžaduje zápis další kód. Další možností je přístup k rozšíření volného typu způsobem. Všechny typy definované v modelu abstraktní data syndikace obsahovat vlastností s názvem `AttributeExtensions` a `ElementExtensions` (s jedinou výjimkou <xref:System.ServiceModel.Syndication.SyndicationContent> má `AttributeExtensions` vlastnost, ale ne `ElementExtensions` vlastnost). Tyto vlastnosti jsou kolekce rozšíření nejsou zpracovávány `TryParseAttribute` a `TryParseElement` metody v uvedeném pořadí. Tato nezpracované rozšíření můžete přejít pomocí volání <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> na `ElementExtensions` vlastnost <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, a <xref:System.ServiceModel.Syndication.SyndicationCategory>. Tato sada metod vyhledá všechna rozšíření se zadaným názvem a obor názvů, deserializuje jednotlivě do instance `TExtension` a vrací je jako kolekce `TExtension` objekty.  
  
## <a name="deriving-a-new-class"></a>Odvození nové třídy  
 Novou třídu můžete odvozen z jakéhokoli z existujících tříd abstraktní data modelu. K tomu při implementaci aplikace, ve kterém mají většinu informační kanály, které pracujete s konkrétní rozšíření. V tomto tématu obsahují většinu informační kanály, které pracoval s `MyExtension` rozšíření. Zajistit lepší programovací prostředí, proveďte následující kroky:  
  
-   Vytvořte třídu, pro uložení dat rozšíření. V takovém případě vytvoření třídy s názvem MyExtension.  
  
-   Odvození třídy s názvem MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> vystavit vlastnost typu MyExtension pro účely programovatelnosti.  
  
-   Přepsání <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> ve třídě MyExtensionItem instanci nové MyExtension při MyExtension se čtou v.  
  
-   Přepsání <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> ve třídě MyExtensionItem zapsat obsah vlastnosti MyExtension do zapisovače XML.  
  
-   Odvození třídy s názvem MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Přepsání <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> ve třídě MyExtensionFeed k vytváření instancí MyExtensionItem místo výchozího <xref:System.ServiceModel.Syndication.SyndicationItem>. Řady metod jsou definovány v <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , můžete vytvořit <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, a <xref:System.ServiceModel.Syndication.SyndicationPerson> objekty (například <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, a <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Všechny z nich může být potlačena za účelem vytvoření vlastní třídy odvozené.  
  
## <a name="see-also"></a>Viz také  
 [Syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Architektura syndikace](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
