---
title: Přidání obchodní logiky pomocí částečných metod
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: e3f82c260a2cab85270a9f33a87eb9a9f04b72c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964146"
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Přidání obchodní logiky pomocí částečných metod
Můžete přizpůsobit Visual Basic a C# generovaný kód v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektech pomocí částečných *metod*. Kód, který [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje, definuje signatury jako jednu část částečné metody. Pokud chcete implementovat metodu, můžete přidat vlastní částečnou metodu. Pokud nepřidáte vlastní implementaci, kompilátor zruší signaturu částečných metod a zavolá výchozí metody v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k přidání ověřování a dalších úprav do tříd entit.  
  
 Například výchozí mapování pro `Customer` třídu v ukázkové databázi Northwind obsahuje následující částečnou metodu:  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Můžete implementovat vlastní metodu přidáním kódu, jako je například následující, do vlastní částečné `Customer` třídy:  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Tento přístup se obvykle používá v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k přepsání výchozích metod pro `Insert`, `Update`, `Delete`a pro ověření vlastností během událostí životního cyklu objektu.  
  
 Další informace naleznete v tématu [částečné metody](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) (Visual Basic) nebo [Partial (metoda) (C# referenční](../../../../../csharp/language-reference/keywords/partial-method.md) dokumentace)C#().  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje `ExampleClass` , že je možné ho definovat pomocí nástroje pro generování kódu, jako je SQLMetal, a potom jak můžete implementovat jenom jednu ze dvou metod.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu je použita relace mezi `Shipper` entitami a `Order` . Všimněte si, `InsertShipper` že mezi metodami jsou částečné `DeleteShipper`metody a. Tyto metody přepíšou výchozí částečné metody poskytované [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapováním.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
