---
title: "Vrátí sadu sjednocení dvou sekvencí"
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
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24a3c7e7ee33d616afdbc9651850c10716a0547c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-set-union-of-two-sequences"></a>Vrátí sadu sjednocení dvou sekvencí
Použití <xref:System.Linq.Queryable.Union%2A> operátor vrátit sadu sjednocení dvou pořadí.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Union%2A> vrátit sekvenci všech zemí, ve kterém jsou buď `Customers` nebo `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operátor je definována pro multisets jako neuspořádaný zřetězení multisets (efektivně výsledek `UNION ALL` klauzule v systému SQL).  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
