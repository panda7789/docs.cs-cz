---
title: Manipulace s daty v datové tabulce
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: 421680a4f39dd68c09dfe20e62f2eec86259b9f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786149"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="6ea11-102">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="6ea11-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="6ea11-103">Po vytvoření <xref:System.Data.DataTable> <xref:System.Data.DataSet>v můžete provádět stejné aktivity, které byste měli použít při použití tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="6ea11-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="6ea11-104">V tabulce můžete přidávat, zobrazovat, upravovat a odstraňovat data. můžete monitorovat chyby a události; a můžete zadávat dotazy na data v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6ea11-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="6ea11-105">Při úpravách dat v **objektu DataTable**můžete také ověřit, zda jsou změny přesné, a určit, zda chcete změny programově přijmout nebo odmítnout.</span><span class="sxs-lookup"><span data-stu-id="6ea11-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ea11-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6ea11-106">In This Section</span></span>  
 [<span data-ttu-id="6ea11-107">Přidání dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="6ea11-107">Adding Data to a DataTable</span></span>](adding-data-to-a-datatable.md)  
 <span data-ttu-id="6ea11-108">Vysvětluje, jak vytvořit nové řádky a přidat je do tabulky.</span><span class="sxs-lookup"><span data-stu-id="6ea11-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="6ea11-109">Zobrazení dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="6ea11-109">Viewing Data in a DataTable</span></span>](viewing-data-in-a-datatable.md)  
 <span data-ttu-id="6ea11-110">Popisuje, jak získat přístup k datům v řádku, včetně původní a aktuální verze dat.</span><span class="sxs-lookup"><span data-stu-id="6ea11-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="6ea11-111">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="6ea11-111">The Load Method</span></span>](the-load-method.md)  
 <span data-ttu-id="6ea11-112">Popisuje použití metody **Load** k vyplnění **objektu DataTable** řádky.</span><span class="sxs-lookup"><span data-stu-id="6ea11-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="6ea11-113">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="6ea11-113">DataTable Edits</span></span>](datatable-edits.md)  
 <span data-ttu-id="6ea11-114">Vysvětluje, jak upravit data v řádku, včetně pozastavení změn na řádek, dokud nebudou navržené změny ověřeny a přijaty.</span><span class="sxs-lookup"><span data-stu-id="6ea11-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="6ea11-115">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="6ea11-115">Row States and Row Versions</span></span>](row-states-and-row-versions.md)  
 <span data-ttu-id="6ea11-116">Poskytuje informace o různých stavech řádku.</span><span class="sxs-lookup"><span data-stu-id="6ea11-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="6ea11-117">Odstranění datového řádku</span><span class="sxs-lookup"><span data-stu-id="6ea11-117">DataRow Deletion</span></span>](datarow-deletion.md)  
 <span data-ttu-id="6ea11-118">Popisuje, jak odebrat řádek z tabulky.</span><span class="sxs-lookup"><span data-stu-id="6ea11-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="6ea11-119">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="6ea11-119">Row Error Information</span></span>](row-error-information.md)  
 <span data-ttu-id="6ea11-120">Vysvětluje, jak vložit informace o chybě na řádek, abyste mohli vyřešit problémy s daty v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea11-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="6ea11-121">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="6ea11-121">AcceptChanges and RejectChanges</span></span>](acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="6ea11-122">Vysvětluje, jak přijmout nebo odmítnout změny provedené na řádku.</span><span class="sxs-lookup"><span data-stu-id="6ea11-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea11-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ea11-123">See also</span></span>

- [<span data-ttu-id="6ea11-124">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="6ea11-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="6ea11-125">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="6ea11-125">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="6ea11-126">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6ea11-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
