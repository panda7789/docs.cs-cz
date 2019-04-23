---
title: 'Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 406e44a0ee3b086ceb47b25a80c4fd0ff5a92607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164668"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Postupy: Použití uložených procedur mapovaných pro vícečetné tvary výsledků
Při vícečetné tvary výsledků můžete vrátit uložené procedury, návratový typ nelze silně typováno do obrazec jeden projekce. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vytvářet všechny typy možných projekce, se nemůže vědět, pořadí, ve kterém bude vrácen.  
  
 Tento scénář s uloženými procedurami, které postupně vyvolávají vícečetné tvary výsledků kontrast. Další informace najdete v tématu [jak: Použití uložených procedur mapovaných pro sekvenční tvary výsledků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atributu se použije pro uložené procedury, které vrací více typů výsledků pro určení sady typů procedura může vrátit.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu SQL, tvar výsledek závisí na vstupu (`shape =1` nebo `shape = 2`). Nevíte, které projekce bude vrácen první.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Příklad  
 Podobně jako následujícím kódu můžete použít k provedení tuto uloženou proceduru.  
  
> [!NOTE]
>  Je nutné použít <xref:System.Data.Linq.IMultipleResults.GetResult%2A> vzor, který má získat enumerátor správný typ, na základě vašich znalostí uložené procedury.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
