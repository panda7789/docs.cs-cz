---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423364"
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
|Jakýmikoli|Určuje, zda některé prvky v sekvenci splní podmínku.|Nelze použít.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Nelze použít.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Postupy: Dynamické určování filtrů predikátů za běhu](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [Postupy: vytvoření dotazu na věty obsahující zadanou sadu slov (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
