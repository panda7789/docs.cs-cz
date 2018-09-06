---
title: Metody AcceptChanges a RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 30b2c303b1823430c480f0706500f8f7e7053c4c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880136"
---
# <a name="acceptchanges-and-rejectchanges"></a>Metody AcceptChanges a RejectChanges
Po ověření správnosti změny provedené v datech <xref:System.Data.DataTable>, může přijmout změny pomocí <xref:System.Data.DataRow.AcceptChanges%2A> metodu <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataSet>, který bude nastaven **aktuální** řádek hodnoty, které mají být **původní** hodnoty a nastaví **RowState** vlastnost **Unchanged**. Přijetí nebo zamítnutí změn vymaže si některé **RowError** informace a nastaví **HasErrors** vlastnost **false**. Aktualizace dat ve zdroji dat může také ovlivnit přijetí nebo zamítnutí změn. Další informace najdete v tématu [aktualizace zdroje dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Pokud existují omezení cizího klíče na **DataTable**, změny přijímat nebo odmítat. pomocí **metoda AcceptChanges** a **RejectChanges** se rozšíří na podřízených řádků  **Objekt DataRow** podle **ForeignKeyConstraint.AcceptRejectRule**. Další informace najdete v tématu [omezení datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Následující příklad zkontroluje pro řádky s chybami, řeší chyby, kde je to možné a odmítne řádky, ve kterém k chybě se nepodařilo najít. Všimněte si, že pro vyřešení chyby, **RowError** hodnota je nastaven na prázdný řetězec, příčinou **HasErrors** vlastnost nastavili na **false**. Když všechny řádky s chybami byly vyřešené nebo zamítnuté **metoda AcceptChanges** nazývá potvrďte všechny změny pro celý **DataTable**.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
