---
title: "Vrátí sadu průnik dvou sekvencí"
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
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dea534ef48b1b37d2f603e9c02d015ab1abe9dac
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Vrátí sadu průnik dvou sekvencí
Použití <xref:System.Linq.Queryable.Intersect%2A> operátor vrátit sadu průnik dvou sekvencí.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá <xref:System.Linq.Queryable.Intersect%2A> vrátit pořadí všech zemí, ve kterých `Customers` a `Employees` za provozu.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> operace je dobře definované jenom na sady. Sémantika pro multisets není definován.  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
