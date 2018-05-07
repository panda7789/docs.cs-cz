---
title: Operátory rovnosti
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1e5784de277d59c7bc945cbe7b605653eec7bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
