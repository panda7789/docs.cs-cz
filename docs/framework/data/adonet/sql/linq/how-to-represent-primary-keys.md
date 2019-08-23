---
title: 'Postupy: Znázornění primárních klíčů'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 28c62798f965edfcffe1a156213c2481a8193b49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943530"
---
# <a name="how-to-represent-primary-keys"></a>Postupy: Znázornění primárních klíčů
Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu Určete vlastnost nebo pole představující primární klíč pro sloupec databáze. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje počítané sloupce jako primární klíče.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Určení vlastnosti nebo pole jako primárního klíče  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. Zadejte hodnotu jako `true`.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
