---
title: "Vytváření v zobrazení DataView"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a8529c317025dbabd9c7467557b244b2f452a77
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview"></a>Vytváření v zobrazení DataView
Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>. Můžete použít **DataView** konstruktoru, nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost <xref:System.Data.DataTable>. **DataView** konstruktor nesmí být prázdné nebo může trvat buď **DataTable** jako jeden argument, nebo **DataTable** společně s kritéria filtru, kritéria řazení a řádek Stav filtru. Další informace o další argumenty nejsou k dispozici pro použití s **DataView**, najdete v části [řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Protože index **DataView** vychází i v případě **DataView** je vytvořen a při jejich **řazení**, **RowFilter**, nebo  **Vlastnost RowStateFilter** jsou upraveny vlastnosti Description, dosáhnout optimálního výkonu poskytuje všechny počáteční řazení nebo filtrování kritéria jako argumenty konstruktoru, když vytvoříte **DataView**. Vytváření **DataView** bez zadání kritéria řazení nebo filtr a pak nastavení **řazení**, **RowFilter**, nebo **Vlastnost RowStateFilter** Vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: Jakmile při **DataView** je vytvořen, a znovu jakékoli vlastnosti řazení nebo filtrování jsou změny.  
  
 Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nevyžaduje žádné argumenty, nebudete moci používat **DataView** nastaven **tabulky** vlastnost .  
  
 Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **DataView** konstruktor. A **RowFilter**, **řazení** sloupce a **DataViewRowState** se dodává spolu s **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 Následující příklad kódu ukazuje, jak získat odkaz na výchozí **DataView** z **DataTable** pomocí **výchozí zobrazení** vlastnosti tabulky.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
