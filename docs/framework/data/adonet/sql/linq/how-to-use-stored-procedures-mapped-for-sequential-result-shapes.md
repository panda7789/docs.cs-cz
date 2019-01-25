---
title: 'Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 296870029d2329640466b3a540e9057738173aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495653"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Postupy: Použití uložených procedur mapovaných pro sekvenční tvary výsledků
Tento druh uložené procedury lze generovat více než jeden prvek výsledek, ale vy víte, v jakém pořadí jsou vráceny výsledky. Tento scénář se scénářem, pokud si nejste jisti pořadí vrátí kontrast. Další informace najdete v tématu [jak: Použití uložených procedur mapovaných pro vícečetné tvary výsledků](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Příklad  
 Tady je T-SQL uloženou proceduru, která postupně vrací vícečetné tvary výsledků:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Příklad  
 Podobně jako následujícím kódu můžete použít k provedení tuto uloženou proceduru.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také:
- [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
