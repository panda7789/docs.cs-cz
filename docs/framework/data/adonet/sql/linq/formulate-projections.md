---
title: Formulování projekcí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037905"
---
# <a name="formulate-projections"></a>Formulování projekcí
Následující příklady ukazují jak `select` výroky C# a `Select` v sadě Visual Studio je možné kombinovat s další funkce do formuláře projekce dotazů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) k vrácení sekvence jména kontaktů pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence jména kontaktů a telefonní čísla pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence jména a telefonní čísla pro zaměstnance. `FirstName` a `LastName` pole jsou sloučeny do jednoho pole (`Name`) a `HomePhone` pole bylo přejmenováno na `Phone` ve výsledné pořadí.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *anonymní typy* k vrácení sekvence všech `ProductID`s a počítanou hodnotu s názvem `HalfPrice`. Tato hodnota nastavena `UnitPrice` děleno 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzule C#) a *podmíněný příkaz* k vrácení sekvence název produktu a dostupnost produktů.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá jazyka Visual Basic `Select` – klauzule (`select` klauzule C#) a *známý typ* (název) k vrácení sekvence názvů zaměstnanci.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` a `Where` v jazyce Visual Basic (`select` a `where` v C#) se vraťte *filtrované pořadí* kontaktní názvů pro zákazníky v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Select` klauzule v jazyce Visual Basic (`select` klauzuli v C#) a *anonymní typy* se vraťte *ve tvaru dílčí* data o zákaznících.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vnořené dotazy vrátit následující výsledky:  
  
- Posloupnost všech objednávek a jejich odpovídající `OrderID`s.  
  
- Dílčí sekvenci položek v pořadí, pro kterou se slevou.  
  
- Množství peníze uloženy v případě, že náklady na přesouvání není zahrnutý.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
