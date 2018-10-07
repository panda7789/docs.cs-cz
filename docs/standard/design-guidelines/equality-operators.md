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
ms.openlocfilehash: 27550a8fd8292029cad9c2e699374a190b1a532e
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839352"
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
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
