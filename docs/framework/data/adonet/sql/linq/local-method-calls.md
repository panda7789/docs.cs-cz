---
title: "Volání Local – metoda"
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
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 105814dd45bc8cd07bf25c4972d4d1b3aa93b1f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="local-method-calls"></a>Volání Local – metoda
Volání metody místní je ten, který se spouští v objektu modelu. Volání vzdálené metody je jedna, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá do systému SQL a odesílá k databázovému stroji pro provedení. Volání metody místní jsou potřeba při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemůže překládat volání do SQL. Jinak <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
## <a name="example-1"></a>Příklad 1  
 V následujícím příkladu se `Order` – třída je namapovaný k tabulce objednávky v ukázkové databázi Northwind. Metoda místní instance se přidal k třídě.  
  
 V konstruktoru pro dotaz 1 `Order` třídy se spustí místně. V dotazu 2, pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se pokusila přeložit `LocalInstanceMethod()`do SQL, pokus selže a <xref:System.InvalidOperationException> by být vyvolána výjimka. Ale protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje podporu pro volání metod místní, nebude dotaz2 výjimku.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
