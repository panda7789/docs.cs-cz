---
title: Volání Local – metoda
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 366c174a13e9a1a1928ef943febf199ae8485dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352435"
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
