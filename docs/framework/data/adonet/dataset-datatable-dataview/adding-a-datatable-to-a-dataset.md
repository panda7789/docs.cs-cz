---
title: Přidání datové tabulky do datové sady
description: Chcete-li se dozvědět, jak vytvořit objekty DataTable a přidat je do existující datové sady v ADO.NET, přečtěte si tento ukázkový kód.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 42bd36b394de560884a2ec607f4cbc65d1171e4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286957"
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="cc815-103">Přidání datové tabulky do datové sady</span><span class="sxs-lookup"><span data-stu-id="cc815-103">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="cc815-104">ADO.NET umožňuje vytvářet <xref:System.Data.DataTable> objekty a přidávat je do existujících objektů <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cc815-104">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc815-105">Můžete nastavit informace o omezení pro a <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataColumn.Unique%2A> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="cc815-105">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc815-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc815-106">Example</span></span>  
 <span data-ttu-id="cc815-107">Následující příklad konstrukce vytvoří <xref:System.Data.DataSet> , přidá nový <xref:System.Data.DataTable> objekt do objektu <xref:System.Data.DataSet> a poté přidá <xref:System.Data.DataColumn> do tabulky tři objekty.</span><span class="sxs-lookup"><span data-stu-id="cc815-107">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="cc815-108">Nakonec kód nastaví jeden sloupec jako sloupec primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="cc815-108">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="cc815-109">Rozlišovat velká a malá písmena</span><span class="sxs-lookup"><span data-stu-id="cc815-109">Case Sensitivity</span></span>  
 <span data-ttu-id="cc815-110">Dvě nebo více tabulek nebo vztahů se stejným názvem, ale různými velikostmi písmen, může existovat v <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cc815-110">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cc815-111">V takových případech odkazují odkazy podle názvu na tabulky a relace na velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="cc815-111">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="cc815-112">Například pokud <xref:System.Data.DataSet> **datová sada** obsahuje tabulky **Tabulka1** a **Tabulka1**, měli byste odkazovat na **Tabulka1** podle názvu jako **DataSet. Tables ["Tabulka1"]** a **Tabulka1** jako **DataSet. Tables ["Tabulka1"]**.</span><span class="sxs-lookup"><span data-stu-id="cc815-112">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="cc815-113">Došlo k pokusu o odkaz na jednu z tabulek jako na **datovou sadu. tabulky ["Tabulka1"]** by vygenerovaly výjimku.</span><span class="sxs-lookup"><span data-stu-id="cc815-113">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="cc815-114">Chování rozlišování velkých a malých písmen neplatí, pokud pouze jedna tabulka nebo vztah má konkrétní název.</span><span class="sxs-lookup"><span data-stu-id="cc815-114">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="cc815-115">Například pokud <xref:System.Data.DataSet> má pouze hodnotu **Tabulka1**, můžete na ni odkazovat pomocí **DataSet. Tables ["Tabulka1"]**.</span><span class="sxs-lookup"><span data-stu-id="cc815-115">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc815-116"><xref:System.Data.DataSet.CaseSensitive%2A>Vlastnost <xref:System.Data.DataSet> nemá vliv na toto chování.</span><span class="sxs-lookup"><span data-stu-id="cc815-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="cc815-117">Tato <xref:System.Data.DataSet.CaseSensitive%2A> vlastnost se vztahuje na data v nástroji <xref:System.Data.DataSet> a ovlivňuje řazení, vyhledávání, filtrování, vynucování omezení atd.</span><span class="sxs-lookup"><span data-stu-id="cc815-117">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="cc815-118">Podpora oboru názvů</span><span class="sxs-lookup"><span data-stu-id="cc815-118">Namespace Support</span></span>  
 <span data-ttu-id="cc815-119">Ve verzích ADO.NET starších než 2,0 nemohly mít dvě tabulky stejný název, i když byly v různých oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="cc815-119">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="cc815-120">Toto omezení se odebralo v ADO.NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="cc815-120">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="cc815-121"><xref:System.Data.DataSet>Může obsahovat dvě tabulky, které mají stejnou <xref:System.Data.DataTable.TableName%2A> hodnotu vlastnosti, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="cc815-121">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc815-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc815-122">See also</span></span>

- [<span data-ttu-id="cc815-123">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="cc815-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="cc815-124">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cc815-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
