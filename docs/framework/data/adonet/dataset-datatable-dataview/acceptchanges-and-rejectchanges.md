---
title: Metoda AcceptChanges a RejectChanges
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
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4c7d86aed61957d15d9c37f494bf80088b164dea
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="acceptchanges-and-rejectchanges"></a>Metoda AcceptChanges a RejectChanges
Po ověření správnosti změny dat v <xref:System.Data.DataTable>, může přijmout změny pomocí <xref:System.Data.DataRow.AcceptChanges%2A> metodu <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataSet>, který bude nastaven **aktuální** řádek hodnoty, které mají být **původní** hodnoty a nastaví **RowState** vlastnost **Unchanged**. Přijetí nebo odmítnutí změny vymaže se žádné **RowError** informace a nastaví **HasErrors** vlastnost **false**. Přijetí nebo odmítnutí změny může ovlivnit také aktualizace dat v datovém zdroji. Další informace najdete v tématu [aktualizace zdroje dat s DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Pokud existují omezení cizího klíče na **DataTable**, změny přijetí nebo odmítnutí pomocí **metoda AcceptChanges** a **RejectChanges** rozšířeny podřízené řádky  **DataRow** podle požadavků **ForeignKeyConstraint.AcceptRejectRule**. Další informace najdete v tématu [DataTable omezení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Následující příklad kontroluje řádků s chybami, řeší chyby, kde je to možné a odmítne řádky, kde chyba nelze přeložit. Všimněte si, že pro vyřešit chyby, **RowError** hodnota je nastaven na prázdný řetězec, příčinou **HasErrors** vlastnost, která má být nastavena na **false**. Když všechny řádky s chybami byly vyřešeny nebo zamítnutí, **metoda AcceptChanges** nazývá tak, aby přijímal všechny změny pro celý **DataTable**.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
