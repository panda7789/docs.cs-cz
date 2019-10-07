---
title: 'Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 8378a175ab2479ab9769ca08579e1c89269eaba4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003219"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Postupy: použití uložených procedur mapovaných pro sekvenční obrazce výsledků
Tento druh uložené procedury může generovat více než jeden obrazec výsledku, ale víte, v jakém pořadí se výsledky vrátí. Porovnejte tento scénář se scénářem, ve kterém neznáte sekvenci vrácených možností. Další informace najdete v tématu [Postupy: použití uložených procedur mapovaných pro více obrazců výsledků](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Příklad  
 Zde je T-SQL uložené procedury, která vrací více výsledných tvarů postupně:  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Příklad  
 Chcete-li provést tuto uloženou proceduru, použijte kód podobný následujícímu.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Uložené procedury](stored-procedures.md)
