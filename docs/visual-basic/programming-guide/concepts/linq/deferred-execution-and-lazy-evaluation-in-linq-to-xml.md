---
title: Odložené provedení a opožděné vyhodnocení v LINQ to XML
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 98a5010de6ea7ef46d845c6a921c54d4e7692370
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410809"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)
Operace dotazů a OS se často implementují pro použití odloženého provedení. V tomto tématu najdete vysvětlení požadavků a výhod odloženého provedení a některých důležitých implementací.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené spuštění znamená, že vyhodnocení výrazu je zpožděno, dokud není skutečně vyžadováno jeho *realizovaná* hodnota. Odložené provádění může významně zlepšit výkon, pokud je třeba manipulovat s velkými datovými kolekcemi, zejména v programech, které obsahují sérii zřetězených dotazů nebo manipulace. V nejlepším případě se odložené spouštění povoluje pouze jedna iterace prostřednictvím zdrojové kolekce.  
  
 Technologie LINQ využívají odložené spouštění jak v rámci členů základních <xref:System.Linq?displayProperty=nameWithType> tříd, tak v metodách rozšíření v různých oborech názvů LINQ, jako je například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> .  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager vs. opožděné hodnocení  
 Když napíšete metodu, která implementuje odložené vykonání, je také nutné rozhodnout, zda implementovat metodu pomocí opožděného vyhodnocení nebo vyhodnocení Eager.  
  
- V *opožděném vyhodnocení*je během každého volání iterátoru zpracován jediný element zdrojové kolekce. Toto je typický způsob, jakým jsou implementovány iterátory.  
  
- Při *vyhodnocování Eager*bude první volání iterátoru mít za následek zpracování celé kolekce. Může být také nutné zadat dočasnou kopii zdrojové kolekce. Například <xref:System.Linq.Enumerable.OrderBy%2A> Metoda musí seřadit celou kolekci před tím, než vrátí první prvek.  
  
 Opožděné hodnocení obvykle poskytuje lepší výkon, protože distribuuje režijní náklady rovnoměrně během hodnocení kolekce a minimalizuje používání dočasných dat. Samozřejmě není pro některé operace žádná jiná možnost než vyhodnotit mezilehlé výsledky.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu znázorňuje odložené provádění:  
  
- [Příklad odloženého provedení (Visual Basic)](deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také

- [Kurz: odložené provádění (Visual Basic)](tutorial-deferred-execution.md)
- [Koncepty a terminologie (funkce Transformation) (Visual Basic)](concepts-and-terminology-functional-transformation.md)
- [Agregační operace (Visual Basic)](aggregation-operations.md)
