---
title: Formulovali projekce
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
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 67c196b5c693e36e45d4cad4fa75e08145dd699d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-projections"></a>Formulovali projekce
Následující příklady zobrazují jak `select` příkaz v jazyce C# a `Select` příkaz v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] zkombinovat s jinými funkcemi do formuláře dotazu projekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) se vrátíte pořadí kontaktní názvů pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* se vrátíte pořadí názvů kontaktní telefonní čísla pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* se vrátíte pořadí názvů telefonní čísla pro zaměstnance. `FirstName` a `LastName` pole jsou sloučeny do jednoho pole (`Name`) a `HomePhone` pole je přejmenován na `Phone` v výsledné pořadí.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* vrátit pořadí všech `ProductID`s a počítanou hodnotu s názvem `HalfPrice`. Tato hodnota nastavena na `UnitPrice` dělený 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *podmíněného příkaz* vrátit pořadí název produktu a dostupnosti produktu.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` – klauzule (`select` klauzule v jazyce C#) a *známý typ* (název) vrátit posloupnost jména zaměstnanců.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` a `Where` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` a `where` v jazyce C#) se vrátíte *filtrované pořadí* kontaktní názvů zákazníků v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzule v jazyce C#) a *anonymní typy* vrátit *ve tvaru podmnožina* dat o zákaznících.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vnořené dotazy vrátit následující výsledky:  
  
-   Pořadí všechny objednávek a jejich odpovídajících `OrderID`s.  
  
-   Dalším položek v pořadí, pro kterou je slevu.  
  
-   Množství peníze uloženy v případě, že náklady na přesouvání není zahrnutý.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
