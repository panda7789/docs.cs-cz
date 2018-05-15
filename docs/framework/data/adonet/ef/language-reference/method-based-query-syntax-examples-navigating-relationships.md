---
title: 'Příklady syntaxe dotazů metoda: Navigace relací'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 6435cf097b2fab880271d2c79ac8bb1afaf9cb6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="9b022-102">Příklady syntaxe dotazů metoda: Navigace relací</span><span class="sxs-lookup"><span data-stu-id="9b022-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="9b022-103">Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou vlastnosti zástupce používaná k nalezení entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="9b022-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="9b022-104">Navigační vlastnosti umožnit uživateli přejít z jedné entity, nebo z jedné entity, která má entit v relaci prostřednictvím přidružení nastavit.</span><span class="sxs-lookup"><span data-stu-id="9b022-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="9b022-105">Toto téma obsahuje příklady syntaxe dotazů metoda procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="9b022-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="9b022-106">Model prodeje společnosti AdventureWorks použít v těchto příkladech je sestaven z kontaktu, adresu, produktu, SalesOrderHeader a podrobnosti prodejní objednávky tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9b022-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9b022-107">V příkladech v tomto tématu použijte následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="9b022-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="9b022-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b022-108">Example</span></span>  
 <span data-ttu-id="9b022-109">Následující příklad v používá syntaxi dotazu na základě metod <xref:System.Linq.Queryable.SelectMany%2A> metoda získat všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="9b022-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="9b022-110">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="9b022-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="9b022-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b022-111">Example</span></span>  
 <span data-ttu-id="9b022-112">V následujícím příkladu v syntaxi dotazu na základě metod <xref:System.Linq.Queryable.Select%2A> metodu za účelem získání všech kontakt ID a součet celkový splatnosti, obraťte se na každý jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="9b022-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="9b022-113">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="9b022-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9b022-114">`Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro součet celkové kvůli všech objednávek pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="9b022-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="9b022-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b022-115">Example</span></span>  
 <span data-ttu-id="9b022-116">Následující příklad syntaxe dotazů metoda získá všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="9b022-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="9b022-117">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce z `SalesOrderHeader` objekty pro každý kontakt.</span><span class="sxs-lookup"><span data-stu-id="9b022-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9b022-118">Jméno kontaktu a objednávky jsou vráceny v instanci anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="9b022-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="9b022-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b022-119">Example</span></span>  
 <span data-ttu-id="9b022-120">Následující příklad používá `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` navigačních vlastností pro získání kolekce z `Address` a `Contact` objekty přidružené k každý pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b022-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="9b022-121">Příjmení kontaktu, adresu, prodeje pořadí číslo a celkový počet splatnosti pro každé pořadí města Seattle jsou vráceny v instanci anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="9b022-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="9b022-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b022-122">Example</span></span>  
 <span data-ttu-id="9b022-123">Následující příklad používá `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003, a pak používá `order.SalesOrderDetail` navigační vlastnost pro získání podrobností o pro každé pořadí.</span><span class="sxs-lookup"><span data-stu-id="9b022-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="9b022-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b022-124">See Also</span></span>  
 [<span data-ttu-id="9b022-125">Navigační vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9b022-125">Navigation Properties</span></span>](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [<span data-ttu-id="9b022-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9b022-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
