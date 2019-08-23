---
title: 'Postupy: Znázornění vypočítaných sloupců'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943535"
---
# <a name="how-to-represent-computed-columns"></a>Postupy: Znázornění vypočítaných sloupců
Použijte vlastnost u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu pro reprezentaci sloupce, jehož obsah je výsledkem výpočtu. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje počítané sloupce jako primární klíče.  
  
### <a name="to-represent-a-computed-column"></a>Reprezentace vypočítaného sloupce  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. Do <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> vlastnosti přiřaďte řetězcovou reprezentaci vzorce.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
