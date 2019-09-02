---
title: Definování primárních klíčů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: dbfd8a8b207c0da9403ac1f8ab36557c4abe383b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204906"
---
# <a name="defining-primary-keys"></a>Definování primárních klíčů
Tabulka databáze běžně obsahuje sloupec nebo skupinu sloupců, které jednoznačně identifikují jednotlivé řádky v tabulce. Tato identifikace sloupce nebo skupiny sloupců se nazývá primární klíč.  
  
 <xref:System.Data.DataColumn> Pokud identifikujete jeden <xref:System.Data.DataTable.PrimaryKey%2A> jako pro <xref:System.Data.DataTable>, tabulka automaticky nastaví <xref:System.Data.DataColumn.AllowDBNull%2A> vlastnost sloupce na **hodnotu false** a <xref:System.Data.DataColumn.Unique%2A> vlastnost na **hodnotu true**. U primárních klíčů ve více sloupcích je automaticky nastavená pouze vlastnost **AllowDBNull** na **hodnotu false**.  
  
 Vlastnost <xref:System.Data.DataTable> PrimaryKey typu přijímá jako hodnotu pole jednoho nebo více objektů DataColumn, jak je znázorněno v následujících příkladech. První příklad definuje jeden sloupec jako primární klíč.  
  
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
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
