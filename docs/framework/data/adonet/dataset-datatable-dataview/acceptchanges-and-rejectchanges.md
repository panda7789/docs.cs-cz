---
title: Metody AcceptChanges a RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: a8589b157bc2579a03d856b73802abc9a4b42855
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204073"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="af9f8-102">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="af9f8-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="af9f8-103"><xref:System.Data.DataTable>Jakmile ověříte přesnost změn provedených v datech v, můžete přijmout změny <xref:System.Data.DataRow> <xref:System.Data.DataRow.AcceptChanges%2A> pomocí metody, <xref:System.Data.DataTable>nebo <xref:System.Data.DataSet>, která nastaví hodnoty **aktuálního** řádku na hodnotu  **Původní** hodnoty a nastaví vlastnost **RowState** na hodnotu Unchanged.</span><span class="sxs-lookup"><span data-stu-id="af9f8-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="af9f8-104">Přijetí nebo zamítnutí změn vymaže všechny **RowError** informace a vlastnost **HasErrors** nastaví na **hodnotu false**(NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="af9f8-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="af9f8-105">Přijímání nebo zamítnutí změn také může ovlivnit aktualizaci dat ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="af9f8-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="af9f8-106">Další informace najdete v tématu [aktualizace datových zdrojů pomocí datových adaptérů](../updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="af9f8-106">For more information, see [Updating Data Sources with DataAdapters](../updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="af9f8-107">Pokud v **objektu DataTable**existují omezení cizího klíče, změny přijaté nebo odmítnuté metodou **AcceptChanges** a **RejectChanges** se šíří do podřízených řádků objektu **DataRow** podle  **Objekt ForeignKeyConstraint. AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="af9f8-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="af9f8-108">Další informace naleznete v tématu [omezení DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="af9f8-108">For more information, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="af9f8-109">Následující příklad zkontroluje řádky s chybami, vyřeší případné chyby a odmítne řádky, ve kterých nelze chybu vyřešit.</span><span class="sxs-lookup"><span data-stu-id="af9f8-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="af9f8-110">Všimněte si, že pro vyřešené chyby je hodnota **RowError** obnovena na prázdný řetězec, což způsobí, že vlastnost **HasErrors** bude nastavena na **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="af9f8-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="af9f8-111">Když všechny řádky s chybami byly vyřešeny nebo odmítnuty, je volána metoda **AcceptChanges** pro přijetí všech změn pro celý **objekt DataTable**.</span><span class="sxs-lookup"><span data-stu-id="af9f8-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a><span data-ttu-id="af9f8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af9f8-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="af9f8-113">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="af9f8-113">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="af9f8-114">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="af9f8-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
