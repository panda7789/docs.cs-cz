---
title: Operace set (C#)
description: Přečtěte si o operacích set a metodách standardního operátoru dotazu, které provádějí operace Set v LINQ v jazyce C#.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302370"
---
# <a name="set-operations-c"></a>Operace set (C#)
Operace s nastavením v LINQ odkazují na operace dotazů, které tvoří sadu výsledků dotazu založenou na přítomnosti nebo nepřítomnosti ekvivalentních prvků v rámci stejné nebo samostatné kolekce (nebo sady).  
  
 Standardní metody operátoru dotazu, které provádějí operace set, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Odebere z kolekce duplicitní hodnoty.|Neužívá se.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|S výjimkou|Vrátí množinu rozdílů, což znamená prvky jedné kolekce, které se nezobrazují v druhé kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Krývají|Vrátí průnik sady, což znamená prvky, které se zobrazují v každé ze dvou kolekcí.|Neužívá se.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Sjednocení|Vrátí sjednocení set, což znamená jedinečné prvky, které se zobrazí v obou dvou kolekcích.|Neužívá se.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Porovnání operací set  
  
### <a name="distinct"></a>Distinct  
 Následující příklad znázorňuje chování <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody v sekvenci znaků. Vrácená sekvence obsahuje jedinečné prvky ze vstupní sekvence.  
  
 ![Obrázek znázorňující chování odlišného&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>S výjimkou  
 Následující příklad znázorňuje chování nástroje <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> . Vrácená sekvence obsahuje pouze prvky z první vstupní sekvence, které nejsou ve druhé vstupní sekvenci.  
  
 ![Obrázek znázorňující akci s výjimkou&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Zobrazuje chování s výjimkou.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Krývají  
 Následující příklad znázorňuje chování nástroje <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> . Vrácená sekvence obsahuje prvky, které jsou společné pro obě vstupní sekvence.  
  
 ![Obrázek znázorňující průnik dvou sekvencí](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Sjednocení  
 Následující příklad znázorňuje operaci sjednocení na dvou sekvencích znaků. Vrácená sekvence obsahuje jedinečné prvky z obou vstupních sekvencí.  
  
 ![Obrázek znázorňující sjednocení dvou sekvencí.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Postup kombinování a porovnávání kolekcí řetězců (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [Jak najít množinu rozdílů mezi dvěma seznamy (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
