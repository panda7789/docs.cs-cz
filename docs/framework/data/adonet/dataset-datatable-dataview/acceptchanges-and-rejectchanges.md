---
title: Metody AcceptChanges a RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: bbcc666b99c2bade479e5ee51750b043c820845d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172897"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="1b865-102">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="1b865-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="1b865-103">Po ověření správnosti změny provedené v datech <xref:System.Data.DataTable>, může přijmout změny pomocí <xref:System.Data.DataRow.AcceptChanges%2A> metodu <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataSet>, který bude nastaven **aktuální** řádek hodnoty, které mají být **původní** hodnoty a nastaví **RowState** vlastnost **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="1b865-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="1b865-104">Přijetí nebo zamítnutí změn vymaže si některé **RowError** informace a nastaví **HasErrors** vlastnost **false**.</span><span class="sxs-lookup"><span data-stu-id="1b865-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="1b865-105">Aktualizace dat ve zdroji dat může také ovlivnit přijetí nebo zamítnutí změn.</span><span class="sxs-lookup"><span data-stu-id="1b865-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="1b865-106">Další informace najdete v tématu [aktualizace zdroje dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="1b865-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="1b865-107">Pokud existují omezení cizího klíče na **DataTable**, změny přijímat nebo odmítat. pomocí **metoda AcceptChanges** a **RejectChanges** se rozšíří na podřízených řádků  **Objekt DataRow** podle **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="1b865-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="1b865-108">Další informace najdete v tématu [omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="1b865-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="1b865-109">Následující příklad zkontroluje pro řádky s chybami, řeší chyby, kde je to možné a odmítne řádky, ve kterém k chybě se nepodařilo najít.</span><span class="sxs-lookup"><span data-stu-id="1b865-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="1b865-110">Všimněte si, že pro vyřešení chyby, **RowError** hodnota je nastaven na prázdný řetězec, příčinou **HasErrors** vlastnost nastavili na **false**.</span><span class="sxs-lookup"><span data-stu-id="1b865-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="1b865-111">Když všechny řádky s chybami byly vyřešené nebo zamítnuté **metoda AcceptChanges** nazývá potvrďte všechny změny pro celý **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="1b865-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b865-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b865-112">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="1b865-113">Manipulace s daty v datové tabulce</span><span class="sxs-lookup"><span data-stu-id="1b865-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="1b865-114">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="1b865-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
