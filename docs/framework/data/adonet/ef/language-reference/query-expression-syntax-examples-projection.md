---
title: 'Příklady syntaxe výrazů dotazů: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 52681a4035ef55133c6191e7eac2cab7ed36c8fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249336"
---
# <a name="query-expression-syntax-examples-projection"></a>Příklady syntaxe výrazů dotazů: Projekce
Příklady v tomto tématu ukazují, jak použít `Select` metodu `From … From …` a klíčová slova pro dotazování [modelu prodeje AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu. `From … From …`je ekvivalentem `SelectMany` metody na základě dotazu. Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.  
  
 Příklady v tomto tématu používají následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a>Vyberte  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> metodu k vrácení všech řádků `Product` z tabulky a zobrazení názvů produktů.  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení posloupnosti pouze názvů produktů.  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu pro `Product.Name` projektování vlastností a `Product.ProductID` , do sekvence anonymních typů.  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a>Z... Z... Operátor SelectMany  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde `TotalDue` je méně než 500,00.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde byla objednávka vytvořena od 1. října 2002 nebo vyšší.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metody) pro výběr všech objednávek, kde celková objednávka je větší než 10000,00, a používá `From` přiřazení, aby nevyžadovala součet dvakrát.  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](queries-in-linq-to-entities.md)
