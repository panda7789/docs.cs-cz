---
title: 'Postupy: Znázornění sloupců jako členů tříd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793512"
---
# <a name="how-to-represent-columns-as-class-members"></a>Postupy: Znázornění sloupců jako členů tříd
K přidružení pole nebo vlastnosti k databázovému sloupci použijte atribut.<xref:System.Data.Linq.Mapping.ColumnAttribute> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Mapování pole nebo vlastnosti na sloupec databáze  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute> Přidejte atribut k deklaraci vlastnosti nebo pole.  
  
## <a name="example"></a>Příklad  
 Následující kód mapuje `CustomerID` pole `Customer` ve `CustomerID` třídě`Customers` na sloupec v tabulce databáze.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> Vlastnost není nutné zadávat, pokud je možné název odvodit. Pokud název nezadáte, název se považuje za shodný s názvem vlastnosti nebo pole.  
  
## <a name="see-also"></a>Viz také:

- [Objektový model LINQ to SQL](the-linq-to-sql-object-model.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
