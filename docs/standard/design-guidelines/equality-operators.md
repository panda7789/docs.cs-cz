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
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741702"
---
# <a name="equality-operators"></a>Operátory rovnosti
Tato část popisuje přetížení operátorů rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.

 ❌ nepřetížit jeden z operátorů rovnosti a nikoli druhý.

 ✔️ se ujistěte, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti mají přesně stejnou sémantiku a podobné charakteristiky výkonu.

 To často znamená, že `Object.Equals` nutné přepsat při přetížení operátorů rovnosti.

 ❌ Vyhněte se vyvolávání výjimek z operátorů rovnosti.

 Například vrátí hodnotu false, pokud jeden z argumentů má hodnotu null namísto vyvolání `NullReferenceException`.

## <a name="equality-operators-on-value-types"></a>Operátory rovnosti na hodnotových typech
 Pokud je rovnost smysluplná, ✔️ přetížit operátory rovnosti na hodnotových typech.

 Ve většině programovacích jazyků neexistuje žádná výchozí implementace `operator==` pro typy hodnot.

## <a name="equality-operators-on-reference-types"></a>Operátory rovnosti na odkazových typech
 ❌ Vyhněte se přetížení operátorů rovnosti na proměnlivých odkazových typech.

 Mnoho jazyků má předdefinované operátory rovnosti pro typy odkazů. Předdefinované operátory obvykle implementují rovnost odkazů a mnoho vývojářů je překvapeno, pokud je výchozí chování změněno na hodnotu rovnosti.

 Tento problém je zmírnit pro neměnný odkazové typy, protože neměnnosti je mnohem obtížnější si všimnout rozdílu mezi rovností odkazů a rovností hodnot.

 ❌ se vyhnout přetížení operátorů rovnosti na odkazových typech, pokud by implementace byla výrazně pomalejší než referenční rovnost.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)
