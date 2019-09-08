---
title: 'Postupy: Znázornění sloupců jako povolujících hodnoty null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781808"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Postupy: Znázornění sloupců jako povolujících hodnoty null
Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu určete, že sloupec přidružené databáze může obsahovat hodnoty null. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Určení sloupce tak, aby umožňoval hodnoty null  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.  
  
2. `true`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> vlastnosti na.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
