---
title: Formulování projekcí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793828"
---
# <a name="formulate-projections"></a>Formulování projekcí
Následující příklady ukazují, jak `select` lze příkaz v C# příkazu `Select` a v Visual Basic zkombinovat s jinými funkcemi a vytvořit tak projekce dotazů.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Select` klauzuli v klauzuli Visual Basic (`select` klauzule in C#) k vrácení posloupnosti názvů kontaktů pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení posloupnosti jména kontaktů a telefonní čísla pro `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení posloupnosti názvů a telefonních čísel pro zaměstnance. `Phone` `Name` `HomePhone` Pole a jsoukombinovánadojednohopole()apolejevevýslednésekvencipřejmenováno.`LastName` `FirstName`  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *anonymní typy* pro vrácení sekvence všech `ProductID`s a vypočtené hodnoty s názvem. `HalfPrice` Tato hodnota je nastavená na `UnitPrice` děleno 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select` klauzule v klauzuli Visual Basic`select` (klauzule C#in) a *podmíněný příkaz* pro vrácení posloupnosti názvu produktu a dostupnosti produktu.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá klauzuli `Select` Visual Basic (`select` klauzule in C#) a *známý typ* (Name) pro vrácení posloupnosti názvů zaměstnanců.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Příklad  
 `Select` Následující příklad používá a `Where` v Visual Basic (`select` a `where` C#) pro vrácení *filtrované posloupnosti* názvů kontaktů pro zákazníky v Londýně.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použita `Select` klauzule v Visual Basic (`select` klauzule in C#) a *anonymní typy* pro vrácení *podmnožiny* dat o zákaznících.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vnořené dotazy k vrácení následujících výsledků:  
  
- Sekvence všech objednávek a jejich odpovídajících `OrderID`s.  
  
- Dílčí sekvence položek v pořadí, pro které existuje sleva.  
  
- Objem uložených peněz, pokud nejsou zahrnuté náklady na expedici.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
