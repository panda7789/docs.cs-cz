---
title: Operátory rovnosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ae188fc7cd55dd843e93afccbe1ea05575a9c36d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129074"
---
# <a name="equality-operators"></a>Operátory rovnosti
Tato část popisuje přetížení operátory rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.  
  
 **X DO NOT** přetížení jeden operátory rovnosti a ne na druhou.  
  
 **✓ DO** Ujistěte se, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti obsahovat přesně stejnou sémantiku a podobné výkonové charakteristiky.  
  
 To často znamená, že `Object.Equals` musí být přepsána, když jsou přetížené operátory rovnosti.  
  
 **X AVOID** generování výjimek ve operátory rovnosti.  
  
 Vrátí hodnotu false, pokud jeden z argumentů má hodnotu null namísto vyvolání `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operátory rovnosti na hodnotových typech  
 **✓ DO** přetížení operátory rovnosti u typů hodnot, pokud má smysl rovnosti.  
  
 Ve většině programovacích jazyků, neexistuje žádný výchozí implementace `operator==` pro typy hodnot.  
  
## <a name="equality-operators-on-reference-types"></a>Operátory rovnosti na odkazových typech  
 **X AVOID** přetížení operátory rovnosti na proměnlivé odkazové typy.  
  
 Řadu jiných jazyků mají operátory integrované rovnost pro typy odkazů. Integrované operátory obvykle implementují referenční rovnosti a celá řada vývojářů jsou překvapení, když se změní výchozí chování na rovnost hodnot.  
  
 Tento problém je nezměnitelný odkazový typů zmírnit, protože neměnnosti znesnadňuje mnohem Všimněte si rozdílu mezi referenční rovnosti a rovnost hodnot.  
  
 **X AVOID** přetížení operátory rovnosti na odkazových typech Pokud implementace by výrazně pomalejší než referenční rovnosti.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
