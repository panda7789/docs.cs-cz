---
title: Manipulace s daty v DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eb4ecf8996836fde443216f1d9225e8f113b0b7f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="991b3-102">Manipulace s daty v DataTable</span><span class="sxs-lookup"><span data-stu-id="991b3-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="991b3-103">Po vytvoření <xref:System.Data.DataTable> v <xref:System.Data.DataSet>, můžete provést stejný aktivity, které byste při používání tabulky v databázi.</span><span class="sxs-lookup"><span data-stu-id="991b3-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="991b3-104">Můžete přidat, zobrazit, upravit a odstranit data v tabulce. můžete sledovat chyby a události; a můžete dát dotaz na data v tabulce.</span><span class="sxs-lookup"><span data-stu-id="991b3-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="991b3-105">Při změně dat v **DataTable**, můžete také ověřit, zda se změny jsou správné a určení, zda prostřednictvím kódu programu přijmout nebo odmítnout změny.</span><span class="sxs-lookup"><span data-stu-id="991b3-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="991b3-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="991b3-106">In This Section</span></span>  
 [<span data-ttu-id="991b3-107">Přidání dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="991b3-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="991b3-108">Vysvětluje, jak vytvořit nové řádky a přidat je do tabulky.</span><span class="sxs-lookup"><span data-stu-id="991b3-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="991b3-109">Zobrazení dat v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="991b3-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="991b3-110">Popisuje způsob přístupu k datům v řádku, včetně aktuální a původní verze data.</span><span class="sxs-lookup"><span data-stu-id="991b3-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="991b3-111">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="991b3-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="991b3-112">Popisuje použití **zatížení** metoda k vyplnění **DataTable** s řádky.</span><span class="sxs-lookup"><span data-stu-id="991b3-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="991b3-113">Úpravy datových tabulek</span><span class="sxs-lookup"><span data-stu-id="991b3-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="991b3-114">Vysvětluje, jak upravovat data v řádku, včetně změny na řádek, pozastavení, dokud si navrhované změny jsou ověřit a přijmout.</span><span class="sxs-lookup"><span data-stu-id="991b3-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="991b3-115">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="991b3-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="991b3-116">Poskytuje informace o různých stavů řádku.</span><span class="sxs-lookup"><span data-stu-id="991b3-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="991b3-117">Odstranění datového řádku</span><span class="sxs-lookup"><span data-stu-id="991b3-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="991b3-118">Popisuje postup odstranění řádku tabulky.</span><span class="sxs-lookup"><span data-stu-id="991b3-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="991b3-119">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="991b3-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="991b3-120">Vysvětluje, jak k vložení informací o chybách na řádek pro řešení problémů s daty v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="991b3-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="991b3-121">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="991b3-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="991b3-122">Vysvětluje, jak přijmout nebo odmítnout změny provedené na řádek.</span><span class="sxs-lookup"><span data-stu-id="991b3-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991b3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="991b3-123">See Also</span></span>  
 [<span data-ttu-id="991b3-124">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="991b3-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="991b3-125">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="991b3-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="991b3-126">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="991b3-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
