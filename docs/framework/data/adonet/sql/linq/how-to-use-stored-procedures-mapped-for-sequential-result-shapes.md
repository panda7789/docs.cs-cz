---
title: "Postupy: pomocí uložených procedur mapovaný pro sekvenční výsledek tvarů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a136876d358a94bf1b61540c93d10aea42a9798b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a>Postupy: pomocí uložených procedur mapovaný pro sekvenční výsledek tvarů
Tento druh uložené procedury mohou generovat více než jeden výsledek tvaru, ale vy víte, že pořadí, v jakém jsou vráceny výsledky. Tento scénář se scénářem, kde si nejste jisti, pořadí se vrátí protějšek. Další informace najdete v tématu [postupy: použití uložené procedury mapovaný pro více obrazců výsledek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## <a name="example"></a>Příklad  
 Tady je T-SQL uložené procedury, jež vrátí více výsledků obrazců postupně:  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a>Příklad  
 Podobný následujícímu kódu byste použili k spouštět tuto uloženou proceduru.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
