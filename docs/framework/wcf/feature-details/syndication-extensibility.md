---
title: Rozšiřitelnost syndikace
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 226ea682d8b17a818e6d5be2097a19315d106bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170798"
---
# <a name="syndication-extensibility"></a>Rozšiřitelnost syndikace
Rozhraní API syndikace je navržené pro poskytování formátu neutrální programovací model, který umožňuje syndikovaný obsah k zápisu do přenosu v různých formátech. Abstraktní datový model obsahuje následující třídy:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy mapování úzce konstrukce definované ve specifikaci Atom 1.0, i když některé názvy se liší.  
  
 Klíčovou funkcí služby syndikace protokolů je rozšíření. Atom 1.0 i RSS 2.0, přidejte atributy a elementy pro informační kanály syndikace, které nejsou definovány ve specifikaci. Programovací model Windows Communication Foundation (WCF) syndikace nabízí tyto způsoby práce s vlastní atributy a rozšíření volného typu přístup a odvození nové třídy.  
  
## <a name="loosely-typed-access"></a>Přístup volného typu  
 Přidání rozšíření podle odvození nové třídy vyžaduje psaním dalšího kódu. Další možností je přístup k rozšíření volného typu způsobem. Všechny typy definované v modelu syndikace abstraktní data obsahují vlastnosti s názvem `AttributeExtensions` a `ElementExtensions` (s jedinou výjimkou <xref:System.ServiceModel.Syndication.SyndicationContent> má `AttributeExtensions` vlastnost, ale ne `ElementExtensions` vlastnost). Tyto vlastnosti jsou kolekce rozšíření, které nejsou zpracovány `TryParseAttribute` a `TryParseElement` metody v uvedeném pořadí. Tato nezpracované rozšíření se zpřístupní po volání <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> na `ElementExtensions` vlastnost <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, a <xref:System.ServiceModel.Syndication.SyndicationCategory>. Tuto sadu metod najde všechna rozšíření se zadaným názvem a oborem názvů, deserializuje jednotlivě do instance `TExtension` a vrátí je jako kolekci `TExtension` objekty.  
  
## <a name="deriving-a-new-class"></a>Odvození nové třídy  
 Novou třídu lze odvodit z jakékoli existující třídy abstraktní datový model. Proveďte při implementaci ve kterém většinu informační kanály, které pracujete, mají příponu konkrétní aplikace. V tomto tématu obsahují většinu informační kanály, které program pracuje s `MyExtension` rozšíření. Pro zajištění vylepšené programovací prostředí, proveďte následující kroky:  
  
-   Vytvoření třídy k umístění dat rozšíření. V takovém případě vytvořte třídu s názvem MyExtension.  
  
-   Odvodit třídu s názvem MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> vystavit vlastnost typu MyExtension pro účely programování.  
  
-   Přepsat <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> ve třídě MyExtensionItem instanci nové MyExtension při MyExtension je určen pro čtení.  
  
-   Přepsat <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> ve třídě MyExtensionItem zapsat obsah vlastnosti MyExtension do zapisovače XML.  
  
-   Odvodit třídu s názvem MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
-   Přepsat <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> ve třídě MyExtensionFeed pro vytvoření instance MyExtensionItem místo výchozího <xref:System.ServiceModel.Syndication.SyndicationItem>. Řady metod, které jsou definovány v <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> dokáže vytvořit <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory>, a <xref:System.ServiceModel.Syndication.SyndicationPerson> objektů (například <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>, a <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Všechny z nich může být potlačena za účelem vytvořit vlastní odvozenou třídu.  
  
## <a name="see-also"></a>Viz také:

- [Syndikace WCF – přehled](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Architektura syndikace](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
