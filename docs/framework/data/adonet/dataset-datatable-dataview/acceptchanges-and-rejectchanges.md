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
# <a name="acceptchanges-and-rejectchanges"></a>Metody AcceptChanges a RejectChanges
<xref:System.Data.DataTable>Jakmile ověříte přesnost změn provedených v datech v, můžete přijmout změny <xref:System.Data.DataRow> <xref:System.Data.DataRow.AcceptChanges%2A> pomocí metody, <xref:System.Data.DataTable>nebo <xref:System.Data.DataSet>, která nastaví hodnoty **aktuálního** řádku na hodnotu  **Původní** hodnoty a nastaví vlastnost **RowState** na hodnotu Unchanged. Přijetí nebo zamítnutí změn vymaže všechny **RowError** informace a vlastnost **HasErrors** nastaví na **hodnotu false**(NEPRAVDA). Přijímání nebo zamítnutí změn také může ovlivnit aktualizaci dat ve zdroji dat. Další informace najdete v tématu [aktualizace datových zdrojů pomocí datových adaptérů](../updating-data-sources-with-dataadapters.md).  
  
 Pokud v **objektu DataTable**existují omezení cizího klíče, změny přijaté nebo odmítnuté metodou **AcceptChanges** a **RejectChanges** se šíří do podřízených řádků objektu **DataRow** podle  **Objekt ForeignKeyConstraint. AcceptRejectRule**. Další informace naleznete v tématu [omezení DataTable](datatable-constraints.md).  
  
 Následující příklad zkontroluje řádky s chybami, vyřeší případné chyby a odmítne řádky, ve kterých nelze chybu vyřešit. Všimněte si, že pro vyřešené chyby je hodnota **RowError** obnovena na prázdný řetězec, což způsobí, že vlastnost **HasErrors** bude nastavena na **hodnotu false**. Když všechny řádky s chybami byly vyřešeny nebo odmítnuty, je volána metoda **AcceptChanges** pro přijetí všech změn pro celý **objekt DataTable**.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
