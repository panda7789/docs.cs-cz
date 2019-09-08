---
title: 'Postupy: Znázornění sloupců jako generovaných databází'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: bb9510986581ad6d3bcd0711aed681ef3a7c4e45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781779"
---
# <a name="how-to-represent-columns-as-database-generated"></a>Postupy: Znázornění sloupců jako generovaných databází
Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu určete pole nebo vlastnost, která představuje sloupec generovaný databází. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>Určení pole nebo vlastnosti jako reprezentace sloupce generovaného databází  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. Nastavte hodnotu vlastnosti na `true`.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
