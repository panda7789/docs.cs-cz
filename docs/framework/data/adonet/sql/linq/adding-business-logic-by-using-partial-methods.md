---
title: Přidání obchodní logiky pomocí částečných metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: ea7dbc4f760a446440cb7291413d69b1202f80e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033836"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Přidání obchodní logiky pomocí částečných metod
Můžete přizpůsobit jazyka Visual Basic a C# generovaného kódu v vaše [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektů s použitím *částečné metody*. Kód, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vygeneruje podpisy definuje částečné metody v rámci jedné. Pokud chcete implementovat metodu, můžete přidat vlastní částečnou metodu. Pokud nemůžete přidat vlastní implementaci, kompilátor zahodí podpis částečné metody a volání výchozí metody [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] přidat ověřování a další vlastní nastavení do tříd entit.  
  
 Například výchozí mapování `Customer` třída v ukázkové databázi Northwind zahrnuje následující částečné metody:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Můžete implementovat vlastní metodu tak, že přidáte následující kód k vlastním částečné `Customer` třídy:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Tento přístup se obvykle používá v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přepsat výchozí metody pro `Insert`, `Update`, `Delete`a pro vlastnosti ověření během události životního cyklu objektu.  
  
 Další informace najdete v tématu [částečné metody](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) nebo [partial (metoda) (C# odkaz)](~/docs/csharp/language-reference/keywords/partial-method.md) (C#).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje `ExampleClass` nejprve může být definovaná generování kódu nástroje, jako je SQLMetal a jak může implementovat jenom jedním ze dvou způsobů.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad používá vztah mezi `Shipper` a `Order` entity. Mějte na paměti mezi metody částečné metody `InsertShipper` a `DeleteShipper`. Tyto metody přepsat výchozí částečné metody poskytnuté [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapování.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
