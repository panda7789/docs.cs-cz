---
title: 'Příklady syntaxe dotazů založených na volání metody: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: c749a7bb1575ee52418f0953ff8216bf4221b674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250152"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="0a236-102">Příklady syntaxe dotazů založených na volání metody: Navigace v relacích</span><span class="sxs-lookup"><span data-stu-id="0a236-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="0a236-103">Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nástroji jsou vlastnosti zkratky používané k vyhledání entit na koncích přidružení.</span><span class="sxs-lookup"><span data-stu-id="0a236-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="0a236-104">Navigační vlastnosti umožňují uživateli přejít z jedné entity na jinou nebo z jedné entity na související entity prostřednictvím sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="0a236-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="0a236-105">V tomto tématu jsou uvedeny příklady syntaxe dotazů založených na metodách, jak procházet vztahy prostřednictvím vlastností navigace v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="0a236-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="0a236-106">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0a236-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0a236-107">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="0a236-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="0a236-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a236-108">Example</span></span>  
 <span data-ttu-id="0a236-109">Následující příklad v syntaxi dotazu založeného na metodách používá <xref:System.Linq.Queryable.SelectMany%2A> metodu k získání všech objednávek kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="0a236-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="0a236-110">Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="0a236-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="0a236-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a236-111">Example</span></span>  
 <span data-ttu-id="0a236-112">Následující příklad v syntaxi dotazu založeného na metodách používá <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktů a součtu celkového počtu všech kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="0a236-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="0a236-113">Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="0a236-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="0a236-114">`Sum` Metoda používávlastnostnavigacekcelkovémusoučtuzdůvodu`Contact.SalesOrderHeader` všech objednávek jednotlivých kontaktů.</span><span class="sxs-lookup"><span data-stu-id="0a236-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="0a236-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a236-115">Example</span></span>  
 <span data-ttu-id="0a236-116">Následující příklad v syntaxi dotazu založeného na metodách získá všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="0a236-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="0a236-117">Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="0a236-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="0a236-118">Jméno kontaktu a objednávky jsou vráceny anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="0a236-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="0a236-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a236-119">Example</span></span>  
 <span data-ttu-id="0a236-120">Následující příklad používá `SalesOrderHeader.Address` navigační vlastnosti a `SalesOrderHeader.Contact` `Address` k získání kolekce objektů a `Contact` přidružených k jednotlivým objednávkám.</span><span class="sxs-lookup"><span data-stu-id="0a236-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="0a236-121">Jméno kontaktu, Adresa ulice, číslo prodejní objednávky a celková hodnota v souvislosti s každým pořadím města v Seattlu jsou vráceny anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="0a236-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="0a236-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a236-122">Example</span></span>  
 <span data-ttu-id="0a236-123">Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003, a poté `order.SalesOrderDetail` používá navigační vlastnost k získání podrobností pro každou objednávku.</span><span class="sxs-lookup"><span data-stu-id="0a236-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="0a236-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a236-124">See also</span></span>

- [<span data-ttu-id="0a236-125">Relace, navigační vlastnosti a cizí klíče</span><span class="sxs-lookup"><span data-stu-id="0a236-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="0a236-126">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0a236-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
