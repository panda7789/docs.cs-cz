---
title: 'Příklady syntaxe výrazů dotazů: Navigace v relacích'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 38a8ddfe4366fefccd0a874a2ad7a20424ef8fac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249473"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="279e8-102">Příklady syntaxe výrazů dotazů: Navigace v relacích</span><span class="sxs-lookup"><span data-stu-id="279e8-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="279e8-103">Navigační vlastnosti v [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nástroji jsou vlastnosti zkratky používané k vyhledání entit na koncích přidružení.</span><span class="sxs-lookup"><span data-stu-id="279e8-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="279e8-104">Navigační vlastnosti umožňují uživateli přejít z jedné entity na jinou nebo z jedné entity na související entity prostřednictvím sady přidružení.</span><span class="sxs-lookup"><span data-stu-id="279e8-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="279e8-105">V tomto tématu najdete příklady v syntaxi výrazů dotazů, jak procházet vztahy prostřednictvím vlastností navigace v LINQ to Entitiesch dotazech.</span><span class="sxs-lookup"><span data-stu-id="279e8-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="279e8-106">Model prodeje společnosti AdventureWorks použitý v těchto příkladech je sestaven z tabulek Contact, adresa, produkt, SalesOrderHeader a SalesOrderDetail v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="279e8-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="279e8-107">Příklady v tomto tématu používají následující `using` / `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="279e8-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="279e8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="279e8-108">Example</span></span>  
 <span data-ttu-id="279e8-109">Následující příklad používá <xref:System.Linq.Queryable.Select%2A> metodu k získání všech ID kontaktů a součtu celkového počtu všech kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="279e8-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="279e8-110">Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="279e8-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="279e8-111">`Sum` Metoda používávlastnostnavigacekcelkovémusoučtuzdůvodu`Contact.SalesOrderHeader` všech objednávek jednotlivých kontaktů.</span><span class="sxs-lookup"><span data-stu-id="279e8-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="279e8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="279e8-112">Example</span></span>  
 <span data-ttu-id="279e8-113">Následující příklad získá všechny objednávky kontaktů, jejichž příjmení je "Zhou".</span><span class="sxs-lookup"><span data-stu-id="279e8-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="279e8-114">Navigační vlastnost se používá k získání `SalesOrderHeader` kolekce objektů pro každý kontakt. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="279e8-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="279e8-115">Jméno kontaktu a objednávky jsou vráceny anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="279e8-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="279e8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="279e8-116">Example</span></span>  
 <span data-ttu-id="279e8-117">`SalesOrderHeader.Address` Následující příklad používá `Contact` navigační `SalesOrderHeader.Contact` vlastnosti a k získání kolekce objektů apřidruženýchkjednotlivýmobjednávkám.`Address`</span><span class="sxs-lookup"><span data-stu-id="279e8-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="279e8-118">Jméno kontaktu, Adresa ulice, číslo prodejní objednávky a celková hodnota v souvislosti s každým pořadím města v Seattlu jsou vráceny anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="279e8-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="279e8-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="279e8-119">Example</span></span>  
 <span data-ttu-id="279e8-120">Následující příklad používá `Where` metodu k vyhledání objednávek, které byly provedeny po 1. prosinci 2003, a poté `order.SalesOrderDetail` používá navigační vlastnost k získání podrobností pro každou objednávku.</span><span class="sxs-lookup"><span data-stu-id="279e8-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="279e8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="279e8-121">See also</span></span>

- [<span data-ttu-id="279e8-122">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="279e8-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
