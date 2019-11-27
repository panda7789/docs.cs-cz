---
title: Odložené provedení a opožděné vyhodnocení v LINQ to XML
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 8e94b9133a2d2dd287fba91600c94460a5204b2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346408"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Odložené provádění a opožděné vyhodnocení v LINQ to XML (Visual Basic)
Operace dotazů a OS se často implementují pro použití odloženého provedení. V tomto tématu najdete vysvětlení požadavků a výhod odloženého provedení a některých důležitých implementací.  
  
## <a name="deferred-execution"></a>Odložené provedení  
 Odložené spuštění znamená, že vyhodnocení výrazu je zpožděno, dokud není skutečně vyžadováno jeho *realizovaná* hodnota. Odložené provádění může významně zlepšit výkon, pokud je třeba manipulovat s velkými datovými kolekcemi, zejména v programech, které obsahují sérii zřetězených dotazů nebo manipulace. V nejlepším případě se odložené spouštění povoluje pouze jedna iterace prostřednictvím zdrojové kolekce.  
  
 Technologie LINQ využívají odložené vykonání v rámci členů základních tříd <xref:System.Linq?displayProperty=nameWithType> třídy i v rozšiřujících metodách v různých oborech názvů LINQ, jako je například <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager vs. opožděné hodnocení  
 Když napíšete metodu, která implementuje odložené vykonání, je také nutné rozhodnout, zda implementovat metodu pomocí opožděného vyhodnocení nebo vyhodnocení Eager.  
  
- V *opožděném vyhodnocení*je během každého volání iterátoru zpracován jediný element zdrojové kolekce. Toto je typický způsob, jakým jsou implementovány iterátory.  
  
- Při *vyhodnocování Eager*bude první volání iterátoru mít za následek zpracování celé kolekce. Může být také nutné zadat dočasnou kopii zdrojové kolekce. Například metoda <xref:System.Linq.Enumerable.OrderBy%2A> musí seřadit celou kolekci před tím, než vrátí první prvek.  
  
 Opožděné hodnocení obvykle poskytuje lepší výkon, protože distribuuje režijní náklady rovnoměrně během hodnocení kolekce a minimalizuje používání dočasných dat. Samozřejmě není pro některé operace žádná jiná možnost než vyhodnotit mezilehlé výsledky.  
  
## <a name="next-steps"></a>Další kroky  
 Další téma v tomto kurzu znázorňuje odložené provádění:  
  
- [Příklad odloženého provedení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Viz také:

- [Kurz: odložené provádění (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Koncepty a terminologie (funkce Transformation) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Agregační operace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
