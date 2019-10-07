---
title: 'Postupy: použití uložených procedur mapovaných pro více obrazců výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 065e866ec5937c4af31c0b1563a7582cb4112eba
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003267"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Postupy: použití uložených procedur mapovaných pro více obrazců výsledků
Pokud uložená procedura může vracet více tvarů výsledků, nemůže být návratový typ silným typem pro jeden obrazec projekce. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] může generovat všechny možné typy projekce, nemůže znát pořadí, ve kterém se budou vracet.  
  
 Porovnejte tento scénář s uloženými procedurami, které vydávají více výsledných tvarů postupně. Další informace najdete v tématu [Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 Atribut <xref:System.Data.Linq.Mapping.ResultTypeAttribute> se použije u uložených procedur, které vracejí více typů výsledků k určení sady typů, které může procedura vracet.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu SQL závisí obrazec výsledků na vstupu (`shape =1` nebo `shape = 2`). Nevíte, které projekce se budou vracet jako první.  
  
``` sql
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
 Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.  
  
> [!NOTE]
> Je nutné použít vzor <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pro získání výčtu správného typu v závislosti na vaší znalosti uložené procedury.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
