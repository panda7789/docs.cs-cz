---
title: Pole návrhu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="field-design"></a>Pole návrhu
Princip zapouzdření je jedním z nejdůležitějších pojmy v objektově orientované návrhu. Tato zásada se zprávou, že data uložená v objektu by měla být přístupné pouze pro tento objekt.  
  
 Užitečný způsob, jak interpretovat princip je to znamená, že by měl být typu navržené tak, aby pole daného typu (název nebo typ změny) můžete měnit, aniž by vás kód jinak než pro členy typu. Tato interpretace okamžitě znamená, že všechna pole musí být privátní.  
  
 Konstanty a statické pole jen pro čtení jsme vyloučit z tohoto striktní omezení, protože takové pole, téměř podle definice nikdy musí změnit.  
  
 **X nesmí** zadejte pole instance, která jsou veřejných nebo chráněný.  
  
 Pro přístup k pole místo provedení je veřejný nebo chráněného by měl poskytovat vlastnosti.  
  
 **PROVEĎTE ✓** pro konstanty, které se budou měnit nikdy používat konstantní pole.  
  
 Kompilátor je nastaven hodnoty polí const přímo do volání kódu. Proto const hodnoty nesmí nikdy změnit bez poškození kompatibility.  
  
 **PROVEĎTE ✓** použít veřejné statické `readonly` pole pro instance předdefinovaných objektů.  
  
 Pokud jsou předdefinované instance typu, deklarujte je jako veřejné jen pro čtení statických polí samotného typu.  
  
 **X nesmí** přiřadit instancí měnitelný typy `readonly` pole.  
  
 Měnitelný typ je typ s instancí, které můžete změnit, jakmile jsou vytvořeny instance. Například pole, většina kolekce a datové proudy jsou měnitelný typy, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, a <xref:System.String?displayProperty=nameWithType> jsou všechny neměnné. Modifikátor jen pro čtení na referenční typ pole brání instance uložené v poli od nahrazují, ale nezabrání data instance pole z upravována volání členové změna instance.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
