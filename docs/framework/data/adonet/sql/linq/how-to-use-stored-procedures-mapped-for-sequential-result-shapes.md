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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a110cf2f321915ef65c571a30a19c5a29bdb8af2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="04a8d-102">Postupy: pomocí uložených procedur mapovaný pro sekvenční výsledek tvarů</span><span class="sxs-lookup"><span data-stu-id="04a8d-102">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>
<span data-ttu-id="04a8d-103">Tento druh uložené procedury mohou generovat více než jeden výsledek tvaru, ale vy víte, že pořadí, v jakém jsou vráceny výsledky.</span><span class="sxs-lookup"><span data-stu-id="04a8d-103">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="04a8d-104">Tento scénář se scénářem, kde si nejste jisti, pořadí se vrátí protějšek.</span><span class="sxs-lookup"><span data-stu-id="04a8d-104">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="04a8d-105">Další informace najdete v tématu [postupy: použití uložené procedury mapovaný pro více obrazců výsledek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="04a8d-105">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04a8d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="04a8d-106">Example</span></span>  
 <span data-ttu-id="04a8d-107">Tady je T-SQL uložené procedury, jež vrátí více výsledků obrazců postupně:</span><span class="sxs-lookup"><span data-stu-id="04a8d-107">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="04a8d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="04a8d-108">Example</span></span>  
 <span data-ttu-id="04a8d-109">Podobný následujícímu kódu byste použili k spouštět tuto uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="04a8d-109">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="04a8d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="04a8d-110">See Also</span></span>  
 [<span data-ttu-id="04a8d-111">Uložené procedury</span><span class="sxs-lookup"><span data-stu-id="04a8d-111">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
