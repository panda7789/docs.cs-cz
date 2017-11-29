---
title: "Příklady syntaxe výrazu dotazu: Navigace relací"
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
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d86fa3aab55daff9c7a3724c93ad68be27a6908b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="84e98-102">Příklady syntaxe výrazu dotazu: Navigace relací</span><span class="sxs-lookup"><span data-stu-id="84e98-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="84e98-103">Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou vlastnosti zástupce používaná k nalezení entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="84e98-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="84e98-104">Navigační vlastnosti umožnit uživateli přejít z jedné entity, nebo z jedné entity, která má entit v relaci prostřednictvím přidružení nastavit.</span><span class="sxs-lookup"><span data-stu-id="84e98-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="84e98-105">Toto téma obsahuje příklady syntaxe výrazu dotazu procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="84e98-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="84e98-106">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="84e98-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="84e98-107">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="84e98-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="84e98-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e98-108">Example</span></span>  
 <span data-ttu-id="84e98-109">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu za účelem získání všech kontakt ID a součet celkový splatnosti, obraťte se na každý jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="84e98-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="84e98-110">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="84e98-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="84e98-111">`Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro součet celkové kvůli všech objednávek pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="84e98-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="84e98-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e98-112">Example</span></span>  
 <span data-ttu-id="84e98-113">Následující příklad načte všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="84e98-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="84e98-114">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="84e98-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="84e98-115">Jméno kontaktu a objednávky jsou vráceny v instanci anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="84e98-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="84e98-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e98-116">Example</span></span>  
 <span data-ttu-id="84e98-117">Následující příklad používá `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` získat navigační vlastnosti kolekce `Address` a `Contact` objekty přidružené k každý pořadí.</span><span class="sxs-lookup"><span data-stu-id="84e98-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="84e98-118">Příjmení kontaktu, adresu, prodeje pořadí číslo a celkový počet splatnosti pro každé pořadí města Seattle jsou vráceny v instanci anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="84e98-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="84e98-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="84e98-119">Example</span></span>  
 <span data-ttu-id="84e98-120">Následující příklad používá `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003, a pak používá `order.SalesOrderDetail` navigační vlastnost pro získání podrobností o pro každé pořadí.</span><span class="sxs-lookup"><span data-stu-id="84e98-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="84e98-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="84e98-121">See Also</span></span>  
 [<span data-ttu-id="84e98-122">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="84e98-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
