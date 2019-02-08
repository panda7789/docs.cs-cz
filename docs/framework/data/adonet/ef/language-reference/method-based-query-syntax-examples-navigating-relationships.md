---
title: 'Příklady syntaxe dotazů založených na volání metody: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: a65b71378b18397e138f88f9b23669e7818feea4
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827445"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="53c68-102">Příklady syntaxe dotazů založených na volání metody: Navigace v relacích</span><span class="sxs-lookup"><span data-stu-id="53c68-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="53c68-103">Vlastnosti navigace v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] jsou místní vlastnosti používaná k nalezení entity na konci přidružení.</span><span class="sxs-lookup"><span data-stu-id="53c68-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="53c68-104">Vlastnosti navigace umožní uživateli se mezi jednotlivými entitami přecházet do druhé nebo z entit souvisejících entit prostřednictvím přidružení nastavení.</span><span class="sxs-lookup"><span data-stu-id="53c68-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="53c68-105">Toto téma obsahuje příklady syntaxe dotazů založených na volání metody procházení vztahů pomocí navigačních vlastností v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="53c68-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="53c68-106">Model prodeje AdventureWorks používá v těchto příkladech je sestaven z tabulky kontaktu, adresa, produktu, SalesOrderHeader a podrobnosti prodejní objednávky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="53c68-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="53c68-107">V příkladech v tomto tématu se používá následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="53c68-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="53c68-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c68-108">Example</span></span>  
 <span data-ttu-id="53c68-109">Následující příklad použití syntaxe dotazů založených na volání metody <xref:System.Linq.Queryable.SelectMany%2A> metodu k získání všech objednávek kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="53c68-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="53c68-110">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="53c68-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="53c68-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c68-111">Example</span></span>  
 <span data-ttu-id="53c68-112">V následujícím příkladu v syntaxi dotazů založených na volání metody <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktu a součet celková částka každý od jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="53c68-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="53c68-113">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="53c68-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="53c68-114">`Sum` Metoda používá `Contact.SalesOrderHeader` navigační vlastnost pro celkový součet vypršení platnosti všech objednávek pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="53c68-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="53c68-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c68-115">Example</span></span>  
 <span data-ttu-id="53c68-116">Následující příklad v syntaxi dotazů založených na volání metody získá všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="53c68-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="53c68-117">`Contact.SalesOrderHeader` Navigační vlastnost se používá k získání kolekce `SalesOrderHeader` objekty pro každého kontaktu.</span><span class="sxs-lookup"><span data-stu-id="53c68-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="53c68-118">Jméno kontaktu a objednávky jsou vráceny v anonymním typu.</span><span class="sxs-lookup"><span data-stu-id="53c68-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="53c68-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c68-119">Example</span></span>  
 <span data-ttu-id="53c68-120">V následujícím příkladu `SalesOrderHeader.Address` a `SalesOrderHeader.Contact` navigačních vlastností pro získání kolekce `Address` a `Contact` objekty přidružené k jednotlivé objednávky.</span><span class="sxs-lookup"><span data-stu-id="53c68-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="53c68-121">Příjmení kontaktu, adresa, prodejní objednávky, čísla a celkový počet termínem pro jednotlivé objednávky na město Seattle jsou vráceny v anonymním typu.</span><span class="sxs-lookup"><span data-stu-id="53c68-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="53c68-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="53c68-122">Example</span></span>  
 <span data-ttu-id="53c68-123">V následujícím příkladu `Where` metody k vyhledání objednávky, které byly provedeny po 1. prosince 2003 a pak použije `order.SalesOrderDetail` vlastnosti navigace použít k získání podrobností každé objednávky.</span><span class="sxs-lookup"><span data-stu-id="53c68-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="53c68-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53c68-124">See also</span></span>
- [<span data-ttu-id="53c68-125">Relace, navigačních vlastností a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="53c68-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="53c68-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="53c68-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
