---
title: 'Příklady syntaxe výrazů dotazů: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 2133ae7902cc4746e00be75e7a801296073041e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614281"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="ec03c-102">Příklady syntaxe výrazů dotazů: Navigace v relacích</span><span class="sxs-lookup"><span data-stu-id="ec03c-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="ec03c-103">Vlastnosti navigace v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou místní vlastnosti používaná k nalezení entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="ec03c-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="ec03c-104">Vlastnosti navigace umožní uživateli se mezi jednotlivými entitami přecházet do druhé nebo z entit souvisejících entit prostřednictvím přidružení nastavení.</span><span class="sxs-lookup"><span data-stu-id="ec03c-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="ec03c-105">Toto téma obsahuje příklady v syntaxe výrazu dotazu procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="ec03c-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="ec03c-106">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ec03c-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ec03c-107">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="ec03c-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="ec03c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec03c-108">Example</span></span>  
 <span data-ttu-id="ec03c-109">V následujícím příkladu <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktu a součet celková částka každý od jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="ec03c-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="ec03c-110">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ec03c-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="ec03c-111">`Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro celkový součet vypršení platnosti všech objednávek pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ec03c-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="ec03c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec03c-112">Example</span></span>  
 <span data-ttu-id="ec03c-113">Následující příklad získá všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="ec03c-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="ec03c-114">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ec03c-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="ec03c-115">Jméno kontaktu a objednávky jsou vráceny v anonymním typu.</span><span class="sxs-lookup"><span data-stu-id="ec03c-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="ec03c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec03c-116">Example</span></span>  
 <span data-ttu-id="ec03c-117">V následujícím příkladu `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` získat navigační vlastnosti kolekce `Address` a `Contact` objekty přidružené k jednotlivé objednávky.</span><span class="sxs-lookup"><span data-stu-id="ec03c-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="ec03c-118">Příjmení kontaktu, adresa, prodejní objednávky, čísla a celkový počet termínem pro jednotlivé objednávky na město Seattle jsou vráceny v anonymním typu.</span><span class="sxs-lookup"><span data-stu-id="ec03c-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="ec03c-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec03c-119">Example</span></span>  
 <span data-ttu-id="ec03c-120">V následujícím příkladu `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak použije `order.SalesOrderDetail` vlastnosti navigace použít k získání podrobností každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="ec03c-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="ec03c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec03c-121">See also</span></span>

- [<span data-ttu-id="ec03c-122">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ec03c-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
