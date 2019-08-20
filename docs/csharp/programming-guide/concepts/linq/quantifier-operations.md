---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 4a0f5b2c90d4b71a945dee02a32cbe897818c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591476"
---
# <a name="quantifier-operations-c"></a>Operace kvantifikátoru (C#)
Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.  
  
 Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích. První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`. Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Všechny|Určuje, zda všechny prvky v sekvenci splní podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|Any|Určuje, zda některé prvky v sekvenci splní podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Obsahuje|Určuje, zda sekvence obsahuje zadaný element.|Není k dispozici.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Postupy: Dynamické určování filtrů predikátů za běhu](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [Postupy: Dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
