---
title: 'Příklady syntaxe výrazů dotazů: Projekce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 9c10c334ae2a10df1f75384ce042781b6f1bd43a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178032"
---
# <a name="query-expression-syntax-examples-projection"></a>Příklady syntaxe výrazů dotazů: Projekce
Příklady v tomto tématu ukazují, jak používat `Select` metoda a `From … From …` klíčová slova k dotazování [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) pomocí syntaxe výrazu dotazu. `From … From …` je ekvivalentní dotaz založený `SelectMany` metody. Prodeje společnosti AdventureWorks model používaný v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.  
  
 V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a>Vyberte  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Linq.Enumerable.Select%2A> metody, která vrátí všechny řádky z `Product` tabulky a zobrazení názvů produktů.  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení sekvence pouze názvy produktů.  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Linq.Queryable.Select%2A> metoda do projektu `Product.Name` a `Product.ProductID` vlastnosti na sekvenci anonymních typů.  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a>Z... Z... (Operátor SelectMany)  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky where `TotalDue` je menší než 500,00.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde byla provedena pořadí 1. října 2002 nebo novější.  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a>Příklad  
 V následujícím příkladu `From … From …` (ekvivalent <xref:System.Linq.Enumerable.SelectMany%2A> metoda) Chcete-li vybrat všechny objednávky, kde je větší než 10000.00 a používá pořadí celkový počet `From` přiřazení žádosti o celkové dvakrát, aby.  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazy v technologii LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
