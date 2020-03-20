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
# <a name="defining-primary-keys"></a><span data-ttu-id="69560-102">Definování primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="69560-102">Defining Primary Keys</span></span>
<span data-ttu-id="69560-103">Databázová tabulka má obvykle sloupec nebo skupinu sloupců, které jednoznačně identifikují každý řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="69560-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="69560-104">Tento identifikační sloupec nebo skupina sloupců se nazývá primární klíč.</span><span class="sxs-lookup"><span data-stu-id="69560-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="69560-105">Když identifikujete <xref:System.Data.DataColumn> jeden <xref:System.Data.DataTable.PrimaryKey%2A> jako <xref:System.Data.DataTable>for , tabulka <xref:System.Data.DataColumn.AllowDBNull%2A> automaticky nastaví vlastnost sloupce <xref:System.Data.DataColumn.Unique%2A> na **false** a vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="69560-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="69560-106">U primárních klíčů s více sloupci je automaticky nastavena na **hodnotu false**pouze vlastnost **AllowDBNull** .</span><span class="sxs-lookup"><span data-stu-id="69560-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="69560-107">**Vlastnost PrimaryKey** <xref:System.Data.DataTable> přijímá jako svou hodnotu pole jednoho nebo více objektů **DataColumn,** jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="69560-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="69560-108">První příklad definuje jeden sloupec jako primární klíč.</span><span class="sxs-lookup"><span data-stu-id="69560-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="69560-109">Následující příklad definuje dva sloupce jako primární klíč.</span><span class="sxs-lookup"><span data-stu-id="69560-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69560-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="69560-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="69560-111">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="69560-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="69560-112">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="69560-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="69560-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69560-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
