---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635480"
---
# <a name="quantifier-operations-c"></a>Operace kvantifikátoru (C#)
Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.  
  
 Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích. První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`. Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Všechny|Určuje, zda všechny prvky v sekvenci splní podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Libovolné|Určuje, zda některé prvky v sekvenci splní podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Nelze použít.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a>Příklady syntaxe výrazů dotazů  
  
### <a name="all"></a>Všechny  
Následující příklad používá `All` ke kontrole, zda mají všechny řetězce určitou délku.
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a>Libovolné  
Následující příklad používá `Any` ke kontrole, zda jsou všechny řetězce začínat na "o".  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a>Obsahuje  
Následující příklad používá `Contains` ke kontrole, zda má pole určitý element.  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Dynamické určování filtrů predikátů při běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
