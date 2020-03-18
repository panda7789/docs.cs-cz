---
title: Odložené spuštění a opožděné vyhodnocení v LINQ na XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594563"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Odložené spuštění a opožděné vyhodnocení v LINQ na XML (C#)
Operace dotazu a osy jsou často implementovány pro použití odložené spuštění. Toto téma vysvětluje požadavky a výhody odložené spuštění a některé důležité informace implementace.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené spuštění znamená, že vyhodnocení výrazu je zpožděno, dokud není jeho realizovaná hodnota skutečně *vyžadována.* Odložené spuštění může výrazně zlepšit výkon, pokud máte manipulovat s rozsáhlými kolekcemi dat, zejména v programech, které obsahují řadu zřetězených dotazů nebo manipulací. V nejlepším případě odložené spuštění umožňuje pouze jednu iteraci prostřednictvím zdrojové kolekce.  
  
 Technologie LINQ rozsáhle využívají odložené provádění v <xref:System.Linq?displayProperty=nameWithType> obou členy základní třídy a v rozšiřujících <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>metod v různých oborech názvů LINQ, jako je například .  
  
 Odložené spuštění je podporována přímo v jazyce C# [yield](../../../language-reference/keywords/yield.md) klíčové slovo (ve formě příkazu) `yield-return` při použití v rámci bloku iterátoru. Takový iterátor musí vrátit kolekci <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> typu nebo (nebo odvozeného typu).  
  
## <a name="eager-vs-lazy-evaluation"></a>Dychtivý vs Lazy Hodnocení  
 Při psaní metody, která implementuje odložené spuštění, musíte se také rozhodnout, zda implementovat metodu pomocí opožděné vyhodnocení nebo eager hodnocení.  
  
- V *opožděné vyhodnocení*, jeden prvek zdrojové kolekce je zpracována během každého volání iterátoru. Jedná se o typický způsob, jakým jsou implementovány iterátory.  
  
- V *eager hodnocení*, první volání iterátoru bude mít za následek zpracování celé kolekce. Může být také vyžadována dočasná kopie zdrojové kolekce. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda má seřadit celou kolekci před vrátí první prvek.  
  
 Opožděné vyhodnocení obvykle poskytuje lepší výkon, protože distribuuje režii zpracování rovnoměrně v průběhu vyhodnocení kolekce a minimalizuje použití dočasných dat. Samozřejmě, že pro některé operace, není jiná možnost, než zhmotnit průběžné výsledky.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu ilustruje odložené spuštění:  
  
- [Příklad odloženého spuštění (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: Řetězení dotazů dohromady (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Pojmy a terminologie (funkční transformace) (C#)](./concepts-and-terminology-functional-transformation.md)
- [Operace agregace (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
