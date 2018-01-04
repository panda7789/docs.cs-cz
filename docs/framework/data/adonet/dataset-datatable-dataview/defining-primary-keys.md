---
title: "Definování primárních klíčů"
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dffced0e3d8cd28699d41ea6bb286e3d59f16bb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="defining-primary-keys"></a>Definování primárních klíčů
Tabulka databáze běžně má sloupec nebo skupiny sloupců, která jednoznačně identifikuje každý řádek v tabulce. Toto identifikační sloupec nebo skupiny sloupců se nazývá primární klíč.  
  
 Při identifikaci jedné <xref:System.Data.DataColumn> jako <xref:System.Data.DataTable.PrimaryKey%2A> pro <xref:System.Data.DataTable>, v tabulce automaticky nastaví <xref:System.Data.DataColumn.AllowDBNull%2A> vlastnost sloupce, který se **false** a <xref:System.Data.DataColumn.Unique%2A> vlastnost  **Hodnota TRUE,**. Pro sloupec primárního klíče, jenom **AllowDBNull** je automaticky nastavena na **false**.  
  
 **PrimaryKey** vlastnost <xref:System.Data.DataTable> obdrží jako svou hodnotu pole jednoho či více **DataColumn** objekty, jak je znázorněno v následujících příkladech. V prvním příkladu definuje jeden sloupec jako primární klíč.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 V následujícím příkladu definuje dva sloupce jako primární klíč.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
