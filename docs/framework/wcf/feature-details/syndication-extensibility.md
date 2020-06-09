---
title: Rozšiřitelnost syndikace
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 5e8f47b45897f46e15847c793c986e953523e66b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600721"
---
# <a name="syndication-extensibility"></a>Rozšiřitelnost syndikace
Syndikace rozhraní API je navrženo tak, aby poskytovalo formátově neutrální programovací model, který umožňuje zápis do sítě v nejrůznějších formátech. Abstraktní datový model se skládá z následujících tříd:  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Tyto třídy jsou úzce mapovány na konstrukce definované ve specifikaci Atom 1,0, i když se některé názvy liší.  
  
 Klíčovou funkcí Syndikačních protokolů je rozšiřitelnost. Oba typy Atom 1,0 a RSS 2,0 přidávají atributy a prvky do kanálů syndikace, které nejsou definovány ve specifikacích. Model programování syndikace Windows Communication Foundation (WCF) poskytuje následující způsoby práce s vlastními atributy a rozšířeními, volně typovaného přístupu a odvozování nové třídy.  
  
## <a name="loosely-typed-access"></a>Volně typovaného přístupu  
 Přidání rozšíření odvozením nové třídy vyžaduje zápis dalšího kódu. Další možností je přístup k rozšířením při volně typovaném způsobu. Všechny typy definované v abstraktním datovém modelu syndikace obsahují vlastnosti s názvem `AttributeExtensions` a `ElementExtensions` (s jednou výjimkou, <xref:System.ServiceModel.Syndication.SyndicationContent> má vlastnost, `AttributeExtensions` ale ne `ElementExtensions` vlastnost). Tyto vlastnosti jsou kolekce rozšíření, která nejsou zpracována `TryParseAttribute` `TryParseElement` metodami a v uvedeném pořadí. K těmto nezpracovaným rozšířením můžete přistupovat voláním <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> `ElementExtensions` vlastnosti <xref:System.ServiceModel.Syndication.SyndicationFeed> ,,, <xref:System.ServiceModel.Syndication.SyndicationItem> <xref:System.ServiceModel.Syndication.SyndicationLink> <xref:System.ServiceModel.Syndication.SyndicationPerson> a <xref:System.ServiceModel.Syndication.SyndicationCategory> . Tato sada metod vyhledá všechna rozšíření se zadaným názvem a oborem názvů, deserializace je jednotlivě do instancí `TExtension` a vrátí je jako kolekci `TExtension` objektů.  
  
## <a name="deriving-a-new-class"></a>Odvození nové třídy  
 Novou třídu můžete odvodit ze všech existujících tříd abstraktních datových modelů. Tento postup proveďte při implementaci aplikace, ve které má většina kanálů, se kterými pracujete, konkrétní rozšíření. V tomto tématu většina kanálů, které program funguje, obsahuje `MyExtension` rozšíření. Chcete-li zajistit lepší programovací prostředí, proveďte následující kroky:  
  
- Vytvořte třídu, která bude uchovávat data rozšíření. V tomto případě vytvořte třídu s názvem MyExtension.  
  
- Odvodit třídu s názvem MyExtensionItem z <xref:System.ServiceModel.Syndication.SyndicationItem> k vystavení vlastnosti typu MyExtension pro účely programovatelnosti.  
  
- Přepište <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> ve třídě MyExtensionItem pro vytvoření instance nové instance MyExtension při čtení MyExtension v.  
  
- Přepsáním <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> třídy MyExtensionItem zapište obsah vlastnosti MyExtension do zapisovače XML.  
  
- Odvodit třídu s názvem MyExtensionFeed z <xref:System.ServiceModel.Syndication.SyndicationFeed> .  
  
- Přepište <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> ve třídě MyExtensionFeed pro vytvoření instance MyExtensionItem namísto výchozího <xref:System.ServiceModel.Syndication.SyndicationItem> . Řada metod je definována v <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> , která může vytvářet <xref:System.ServiceModel.Syndication.SyndicationLink> objekty, <xref:System.ServiceModel.Syndication.SyndicationCategory> , a <xref:System.ServiceModel.Syndication.SyndicationPerson> (například,, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink> <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory> a <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson> ). Všechny, které mohou být přepsány k vytvoření vlastní odvozené třídy.  
  
## <a name="see-also"></a>Viz také

- [Syndikace WCF – přehled](wcf-syndication-overview.md)
- [Architektura syndikace](architecture-of-syndication.md)
