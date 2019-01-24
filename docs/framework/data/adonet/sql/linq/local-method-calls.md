---
title: Volání místních metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: 249ed8425f175b80cb55289c2a7fe68742d8389c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655722"
---
# <a name="local-method-calls"></a>Volání místních metod
Volání místních metod je ten, který se spouští v objektovém modelu. Volání vzdálené metody je jeden, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se přeloží na SQL a odesílá do databázového stroje pro spuštění. Volání místních metod jsou potřeba při [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemůže překládat volání do SQL. V opačném případě <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
## <a name="example-1"></a>Příklad 1  
 V následujícím příkladu `Order` třídy je namapována na tabulce objednávky v ukázkové databázi Northwind. Metoda místní instance byla přidána do třídy.  
  
 V konstruktoru pro dotaz 1 `Order` třídy je spuštěn lokálně. V dotazu 2, pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusila přeložit `LocalInstanceMethod()`do databáze SQL, je tento pokus selže a <xref:System.InvalidOperationException> bude vyvolána výjimka. Ale protože [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje podporu pro volání místních metod, nebude dotaz2 vyvolat výjimku.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
