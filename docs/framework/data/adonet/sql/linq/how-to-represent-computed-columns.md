---
title: 'Postupy: Znázornění vypočítaných sloupců'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: df72562b303e5b9a7c31334df06926f157b59b05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903863"
---
# <a name="how-to-represent-computed-columns"></a>Postupy: Znázornění vypočítaných sloupců
Použití [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnosti <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut k reprezentaci sloupec, jehož obsahem je výsledek výpočtu.  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Počítané sloupce nepodporuje jako primární klíče.  
  
### <a name="to-represent-a-computed-column"></a>K reprezentaci počítaný sloupec  
  
1. Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
2. Přiřadit řetězcovou reprezentaci vzorec tak, aby <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
