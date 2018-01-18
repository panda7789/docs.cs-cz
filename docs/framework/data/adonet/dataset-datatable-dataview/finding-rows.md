---
title: "Vyhledání řádků"
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 43703ead9d38ea1cf02539f12479e9228d7eacd4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="finding-rows"></a><span data-ttu-id="d37af-102">Vyhledání řádků</span><span class="sxs-lookup"><span data-stu-id="d37af-102">Finding Rows</span></span>
<span data-ttu-id="d37af-103">Můžete vyhledat řádků podle jejich hodnot pro klíč řazení s použitím <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="d37af-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="d37af-104">Rozlišování velkých a malých písmen vyhledávání hodnot v **najít** a **FindRows** je dáno metody **CaseSensitive** vlastnost základní <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d37af-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d37af-105">Hledání hodnoty musí odpovídat existující řazení klíčové hodnoty jako celek cílem vrátit výsledek.</span><span class="sxs-lookup"><span data-stu-id="d37af-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="d37af-106">**Najít** metoda vrátí celé číslo s index <xref:System.Data.DataRowView> odpovídající kritériím hledání.</span><span class="sxs-lookup"><span data-stu-id="d37af-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="d37af-107">Pokud více než jeden řádek odpovídá kritéria hledání, pouze index první odpovídající **DataRowView** je vrácen.</span><span class="sxs-lookup"><span data-stu-id="d37af-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="d37af-108">Pokud nejsou nalezeny žádné shody, **najít** vrátí hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="d37af-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="d37af-109">Chcete-li vrátit výsledky hledání, které odpovídají více řádků, použijte **FindRows** metoda.</span><span class="sxs-lookup"><span data-stu-id="d37af-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="d37af-110">**FindRows** funguje stejně jako **najít** metoda, s výjimkou toho, které se vrátí **DataRowView** pole, která odkazuje na všechny odpovídající řádky v **DataView**.</span><span class="sxs-lookup"><span data-stu-id="d37af-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="d37af-111">Pokud nejsou nalezeny žádné shody, **DataRowView** pole bude prázdný.</span><span class="sxs-lookup"><span data-stu-id="d37af-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="d37af-112">Použít **najít** nebo **FindRows** metody, je nutné zadat řazení pořadí buď nastavení **ApplyDefaultSort** k **true** nebo pomocí **Řazení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d37af-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="d37af-113">Pokud není zadaný žádný pořadí řazení, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d37af-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="d37af-114">**Najít** a **FindRows** metody přijímají pole hodnot jako vstup, jehož délka odpovídá počtu sloupců v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="d37af-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="d37af-115">V případě řazení na jeden sloupec můžete předat jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d37af-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="d37af-116">Pro pořadí řazení obsahující více sloupců předáte pole objektů.</span><span class="sxs-lookup"><span data-stu-id="d37af-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="d37af-117">Všimněte si, že pro řazení do více sloupců, hodnoty v poli objektu musí odpovídat pořadí sloupců zadaných v **řazení** vlastnost **DataView**.</span><span class="sxs-lookup"><span data-stu-id="d37af-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="d37af-118">Následující příklad kódu ukazuje **najít** metoda volána proti **DataView** s jedním sloupcem pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="d37af-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="d37af-119">Pokud vaše **řazení** vlastnost určuje více sloupců, je nutné předat pole objektů s hodnotami vyhledávání pro každý sloupec v pořadí zadaném **řazení** vlastnosti, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d37af-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="d37af-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d37af-120">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="d37af-121">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="d37af-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="d37af-122">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d37af-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
