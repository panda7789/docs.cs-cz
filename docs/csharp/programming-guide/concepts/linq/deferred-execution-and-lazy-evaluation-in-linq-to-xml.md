---
title: Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594563"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)
Operace dotazů a OS se často implementují pro použití odloženého provedení. V tomto tématu najdete vysvětlení požadavků a výhod odloženého provedení a některých důležitých implementací.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené spuštění znamená, že vyhodnocení výrazu je zpožděno, dokud není skutečně vyžadováno jeho *realizovaná* hodnota. Odložené provádění může významně zlepšit výkon, pokud je třeba manipulovat s velkými datovými kolekcemi, zejména v programech, které obsahují sérii zřetězených dotazů nebo manipulace. V nejlepším případě se odložené spouštění povoluje pouze jedna iterace prostřednictvím zdrojové kolekce.  
  
 Technologie LINQ využívají odložené spouštění jak v rámci členů základních <xref:System.Linq?displayProperty=nameWithType> tříd, tak v metodách rozšíření v různých oborech názvů LINQ, <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>jako je například.  
  
 Odložené provádění je podporováno přímo v C# jazyce pomocí klíčového slova [yield](../../../language-reference/keywords/yield.md) (ve `yield-return` formě příkazu) při použití v rámci bloku iterátoru. Takový iterátor musí vracet kolekci typu <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> (nebo odvozeného typu).  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager vs. Opožděné hodnocení  
 Když napíšete metodu, která implementuje odložené vykonání, je také nutné rozhodnout, zda implementovat metodu pomocí opožděného vyhodnocení nebo vyhodnocení Eager.  
  
- V *opožděném vyhodnocení*je během každého volání iterátoru zpracován jediný element zdrojové kolekce. Toto je typický způsob, jakým jsou implementovány iterátory.  
  
- Při *vyhodnocování Eager*bude první volání iterátoru mít za následek zpracování celé kolekce. Může být také nutné zadat dočasnou kopii zdrojové kolekce. Například <xref:System.Linq.Enumerable.OrderBy%2A> metoda musí seřadit celou kolekci před tím, než vrátí první prvek.  
  
 Opožděné hodnocení obvykle poskytuje lepší výkon, protože distribuuje režijní náklady rovnoměrně během hodnocení kolekce a minimalizuje používání dočasných dat. Samozřejmě není pro některé operace žádná jiná možnost než vyhodnotit mezilehlé výsledky.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu znázorňuje odložené provádění:  
  
- [Příklad odloženého provedení (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: Zřetězení dotazů společně (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Koncepty a terminologie (funkce Transformation)C#()](./concepts-and-terminology-functional-transformation.md)
- [Agregační operace (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
