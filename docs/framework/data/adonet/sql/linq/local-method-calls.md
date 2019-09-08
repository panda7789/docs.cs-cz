---
title: Volání místních metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: ec288d5ac2f6466860362be82c619c89204e8f31
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781416"
---
# <a name="local-method-calls"></a>Volání místních metod
Volání místní metody je jeden, který je spuštěn v rámci objektového modelu. Vzdálené volání metody je jeden, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se překládá na SQL a odesílá databázovému stroji ke spuštění. Volání místní metody jsou nutná, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Pokud nelze přeložit volání do jazyka SQL. V opačném případě je vyvolána výjimka. <xref:System.InvalidOperationException>  
  
## <a name="example-1"></a>Příklad 1  
 V následujícím příkladu `Order` je třída namapována na tabulku Orders v ukázkové databázi Northwind. Do třídy byla přidána metoda místní instance.  
  
 V dotazu 1 je konstruktor `Order` třídy spouštěn místně. Pokud [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] se při pokusu o překlad do `LocalInstanceMethod()`kódu SQL pokusil <xref:System.InvalidOperationException> o převod na SQL, pokus selže a vyvolá se výjimka. Ale vzhledem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k tomu, že poskytuje podporu pro volání místních metod, query2 nevyvolá výjimku.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
