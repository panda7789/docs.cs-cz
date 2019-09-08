---
title: 'Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793497"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Postupy: Znázornění sloupců jako sloupců časového razítka nebo verze
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Pomocí<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnosti atributu<xref:System.Data.Linq.Mapping.ColumnAttribute> určete pole nebo vlastnost, které představují sloupec databáze, který obsahuje časové razítka databáze nebo čísla verzí.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Určení pole nebo vlastnosti představující sloupec časového razítka nebo verze  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. `true`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> vlastnosti na.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Určení členů, kteří jsou testováni pro konflikty souběžnosti](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
