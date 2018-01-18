---
title: "Vrátí první prvek v pořadí"
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
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bbdfe78f15490ce2c6722c83a4615ca29cbc5863
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-first-element-in-a-sequence"></a>Vrátí první prvek v pořadí
Použití <xref:System.Linq.Enumerable.First%2A> operátor vrátit první prvek v pořadí. Dotazy, které používají <xref:System.Linq.Enumerable.First%2A> okamžitě prováděny.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nepodporuje <xref:System.Linq.Enumerable.Last%2A> operátor.  
  
## <a name="example"></a>Příklad  
 Následující kód najde první `Shipper` v tabulce:  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, jsou výsledky  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Příklad  
 Následující kód najde jedné `Customer` který má `CustomerID` BONAP.  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, jsou výsledky `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
