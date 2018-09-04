---
title: Manipulace s daty v datové tabulce
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: a09edc6ce3098ab135d8c27ba0f6ad56cceed159
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521305"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="5a0d8-102">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="5a0d8-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="5a0d8-103">Po vytvoření <xref:System.Data.DataTable> v <xref:System.Data.DataSet>, můžete provést stejný aktivity, které byste použili tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="5a0d8-104">Můžete přidat, zobrazit, upravit a odstranit data v tabulce. můžete sledovat chyby a události; a můžete zadat dotaz data v tabulce.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="5a0d8-105">Při změně dat v **DataTable**, můžete si taky ověřit, zda změny jsou správné a určete, zda prostřednictvím kódu programu přijmout nebo odmítnout změny.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a0d8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="5a0d8-106">In This Section</span></span>  
 [<span data-ttu-id="5a0d8-107">Přidání dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="5a0d8-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="5a0d8-108">Vysvětluje, jak vytvořit nové řádky a přidat je do tabulky.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="5a0d8-109">Zobrazení dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="5a0d8-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="5a0d8-110">Popisuje, jak získat přístup k datům v řádku, včetně aktuální a původní verze data.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="5a0d8-111">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="5a0d8-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="5a0d8-112">Popisuje použití **zatížení** metodu tak, aby vyplnil **DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="5a0d8-113">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="5a0d8-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="5a0d8-114">Vysvětluje, jak upravovat data v řádku, včetně pozastavení změny na řádek, dokud je ověřeno a přijato navrhovaných změn.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="5a0d8-115">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="5a0d8-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="5a0d8-116">Poskytuje informace o různých státech řádek.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="5a0d8-117">Odstranění datového řádku</span><span class="sxs-lookup"><span data-stu-id="5a0d8-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="5a0d8-118">Popisuje, jak odebrat řádek z tabulky.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="5a0d8-119">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="5a0d8-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="5a0d8-120">Vysvětluje, jak vložit informace o chybě na řádku, který vám pomůže vyřešit problémy s daty v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="5a0d8-121">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="5a0d8-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="5a0d8-122">Vysvětluje, jak přijmout nebo odmítnout změny provedené na řádek.</span><span class="sxs-lookup"><span data-stu-id="5a0d8-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a0d8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a0d8-123">See Also</span></span>  
 [<span data-ttu-id="5a0d8-124">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5a0d8-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="5a0d8-125">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5a0d8-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="5a0d8-126">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="5a0d8-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
