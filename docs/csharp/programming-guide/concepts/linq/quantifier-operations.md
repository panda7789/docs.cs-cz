---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635480"
---
# <a name="quantifier-operations-c"></a>Operace kvantifikátoru (C#)
Kvantifikátor <xref:System.Boolean> operace vrátit hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splňují podmínku.  
  
 Následující obrázek znázorňuje dvě různé kvantifikátory ve dvou různých zdrojových sekvencích. První operace se zeptá, zda jeden nebo více prvků je znak `true`'A', a výsledek je . Druhá operace se zeptá, zda jsou všechny prvky znakem A a výsledek je `true`.  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Všechny|Určuje, zda všechny prvky v sekvenci splňují podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Všechny|Určuje, zda některé prvky v sekvenci splňují podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Contains|Určuje, zda sekvence obsahuje zadaný prvek.|Neužívá se.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazu dotazu  
  
### <a name="all"></a>Všechny  
Následující příklad používá `All` ke kontrole, že všechny řetězce mají určitou délku.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Všechny  
Následující příklad používá `Any` ke kontrole, že všechny řetězce jsou začínat 'o'.  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Contains  
Následující příklad používá `Contains` ke kontrole pole mají určitý prvek.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Dynamické určování filtrů predikátů při běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
