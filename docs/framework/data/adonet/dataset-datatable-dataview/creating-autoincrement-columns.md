---
title: "Vytváření AutoIncrement sloupců"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0cef5944db5e926a4b2d81fd226abc9691b6d1bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="87827-102">Vytváření AutoIncrement sloupců</span><span class="sxs-lookup"><span data-stu-id="87827-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="87827-103">Aby jedinečný sloupec hodnoty, můžete nastavit hodnoty ve sloupcích se zvýší automaticky při přidávání řádků do tabulky.</span><span class="sxs-lookup"><span data-stu-id="87827-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="87827-104">Chcete-li vytvořit automaticky rostoucí <xref:System.Data.DataColumn>, nastavte <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnost sloupce, který se **true**.</span><span class="sxs-lookup"><span data-stu-id="87827-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="87827-105"><xref:System.Data.DataColumn> Pak začíná hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementSeed%2A> vlastnost a s každým řádkem přidat hodnotu **AutoIncrement** sloupec zvyšuje úroveň hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementStep%2A> vlastnost sloupce.</span><span class="sxs-lookup"><span data-stu-id="87827-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="87827-106">Pro **AutoIncrement** sloupců, doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** nastavit na **true**.</span><span class="sxs-lookup"><span data-stu-id="87827-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="87827-107">Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnota 200 a přidá postupně v krocích 3.</span><span class="sxs-lookup"><span data-stu-id="87827-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="87827-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="87827-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="87827-109">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="87827-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="87827-110">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="87827-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="87827-111">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="87827-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
