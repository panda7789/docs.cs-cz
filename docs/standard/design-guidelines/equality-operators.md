---
title: "Operátory rovnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a>Operátory rovnosti
Tato část popisuje přetížení operátory rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.  
  
 **X nesmí** přetížení jeden operátory rovnosti a ne na druhou.  
  
 **PROVEĎTE ✓** Ujistěte se, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti obsahovat přesně stejnou sémantiku a podobné výkonové charakteristiky.  
  
 To často znamená, že `Object.Equals` musí být potlačena, pokud jsou přetížené operátory rovnosti.  
  
 **X nepoužívejte** generování výjimek ve operátory rovnosti.  
  
 Vrátí hodnotu false, pokud jeden z argumentů hodnotu null místo vyvolání `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operátory rovnosti u typů hodnot  
 **PROVEĎTE ✓** přetížení operátory rovnosti u typů hodnot, pokud má smysl rovnosti.  
  
 Ve většině programovacích jazyků, neexistuje žádný výchozí implementaci třídy `operator==` u typů hodnot.  
  
## <a name="equality-operators-on-reference-types"></a>Operátory rovnosti na odkazových typech  
 **X nepoužívejte** přetížení operátory rovnosti na proměnlivé odkazové typy.  
  
 Mnoho jazyky mají operátory rovnosti předdefinované pro odkazové typy. Předdefinované operátory obvykle implementovat referenční rovnosti a když se změní výchozí chování na rovnosti hodnoty překvapil celá řada vývojářů.  
  
 Protože neměnitelnosti znesnadňuje mnohem Všimněte rozdíl mezi referenční rovnosti a rovnosti hodnoty pro neměnné odkazové typy zmírnit tento problém.  
  
 **X nepoužívejte** přetížení operátory rovnosti na odkazových typech Pokud implementace by výrazně pomalejší než referenční rovnosti.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny týkající se používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
