---
title: Definování primárních klíčů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 0f87b1b730eecf0edad75bd87ca8b491b96e1d2b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784706"
---
# <a name="defining-primary-keys"></a>Definování primárních klíčů
Tabulka databáze běžně obsahuje sloupec nebo skupinu sloupců, které jednoznačně identifikují jednotlivé řádky v tabulce. Tato identifikace sloupce nebo skupiny sloupců se nazývá primární klíč.  
  
 <xref:System.Data.DataColumn> Pokud identifikujete jeden <xref:System.Data.DataTable.PrimaryKey%2A> jako pro <xref:System.Data.DataTable>, tabulka automaticky nastaví <xref:System.Data.DataColumn.AllowDBNull%2A> vlastnost sloupce na **hodnotu false** a <xref:System.Data.DataColumn.Unique%2A> vlastnost na **hodnotu true**. U primárních klíčů ve více sloupcích je automaticky nastavená pouze vlastnost **AllowDBNull** na **hodnotu false**.  
  
 Vlastnost<xref:System.Data.DataTable> **PrimaryKey** typu přijímá jako hodnotu pole jednoho nebo více objektů **DataColumn** , jak je znázorněno v následujících příkladech. První příklad definuje jeden sloupec jako primární klíč.  
  
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
  
 Následující příklad definuje dva sloupce jako primární klíč.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataTable>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové tabulky](datatables.md)
- [Přehled ADO.NET](../ado-net-overview.md)
