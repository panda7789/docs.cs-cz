---
title: 'Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: bae10e823a274304f21292cf55947a4d4eaccc10
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781466"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků
Tento druh uložené procedury může generovat více než jeden obrazec výsledku, ale víte, v jakém pořadí se výsledky vrátí. Porovnejte tento scénář se scénářem, ve kterém neznáte sekvenci vrácených možností. Další informace najdete v tématu [jak: Použití uložených procedur mapovaných pro více tvarů](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)výsledků.  
  
## <a name="example"></a>Příklad  
 Zde je T-SQL uložené procedury, která vrací více výsledných tvarů postupně:  
  
```  
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
