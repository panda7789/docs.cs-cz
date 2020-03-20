---
title: Definování primárních klíčů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151179"
---
# <a name="defining-primary-keys"></a>Definování primárních klíčů
Databázová tabulka má obvykle sloupec nebo skupinu sloupců, které jednoznačně identifikují každý řádek v tabulce. Tento identifikační sloupec nebo skupina sloupců se nazývá primární klíč.  
  
 Když identifikujete <xref:System.Data.DataColumn> jeden <xref:System.Data.DataTable.PrimaryKey%2A> jako <xref:System.Data.DataTable>for , tabulka <xref:System.Data.DataColumn.AllowDBNull%2A> automaticky nastaví vlastnost sloupce <xref:System.Data.DataColumn.Unique%2A> na **false** a vlastnost **true**. U primárních klíčů s více sloupci je automaticky nastavena na **hodnotu false**pouze vlastnost **AllowDBNull** .  
  
 **Vlastnost PrimaryKey** <xref:System.Data.DataTable> přijímá jako svou hodnotu pole jednoho nebo více objektů **DataColumn,** jak je znázorněno v následujících příkladech. První příklad definuje jeden sloupec jako primární klíč.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataTable>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové tabulky](datatables.md)
- [Přehled ADO.NET](../ado-net-overview.md)
