---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: e5a48c5caf9239e0e7b7f2e7a3ad8ab5df168ba1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684187"
---
# <a name="finding-rows"></a><span data-ttu-id="398ae-102">Hledání řádků</span><span class="sxs-lookup"><span data-stu-id="398ae-102">Finding Rows</span></span>
<span data-ttu-id="398ae-103">Můžete hledat pomocí řádků podle jejich hodnoty klíče řazení <xref:System.Data.DataView.Find%2A> a <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="398ae-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="398ae-104">Rozlišování velikosti písmen vyhledávání hodnoty v **najít** a **FindRows** metody je určeno **CaseSensitive** vlastnost základního <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="398ae-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="398ae-105">Hledání hodnoty musí odpovídat existující hodnoty klíče řazení v plné výši k vrácení výsledku.</span><span class="sxs-lookup"><span data-stu-id="398ae-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="398ae-106">**Najít** metoda vrátí celé číslo s indexem <xref:System.Data.DataRowView> , které by odpovídalo kritériím hledání.</span><span class="sxs-lookup"><span data-stu-id="398ae-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="398ae-107">Pokud více než jeden řádek odpovídá kritériím hledání, pouze index první odpovídající **DataRowView** je vrácena.</span><span class="sxs-lookup"><span data-stu-id="398ae-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="398ae-108">Pokud se nenajdou žádné shody, **najít** vrátí hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="398ae-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="398ae-109">Chcete-li vrátit výsledky hledání, které odpovídají více řádků, použijte **FindRows** metody.</span><span class="sxs-lookup"><span data-stu-id="398ae-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="398ae-110">**FindRows** funguje stejně jako **najít** metody, s tím rozdílem, že se vrátí **DataRowView** pole, které odkazuje na všechny odpovídající řádky **DataView**.</span><span class="sxs-lookup"><span data-stu-id="398ae-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="398ae-111">Pokud se nenajdou žádné shody, **DataRowView** pole bude prázdný.</span><span class="sxs-lookup"><span data-stu-id="398ae-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="398ae-112">Použít **najít** nebo **FindRows** metod je nutné zadat řazení order buď nastavením **ApplyDefaultSort** k **true** nebo s použitím **Řazení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="398ae-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="398ae-113">Pokud není zadána žádná pořadí řazení, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="398ae-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="398ae-114">**Najít** a **FindRows** metody pole hodnot, které přijímají jako vstup, jehož délka shoduje s počtem sloupců v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="398ae-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="398ae-115">V případě řazení na jeden sloupec můžete předat hodnotu single.</span><span class="sxs-lookup"><span data-stu-id="398ae-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="398ae-116">Pro pořadí řazení, který obsahuje více sloupců můžete předat pole objektů.</span><span class="sxs-lookup"><span data-stu-id="398ae-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="398ae-117">Všimněte si, že pro řazení do více sloupců, hodnoty v poli objektu musí odpovídat pořadí sloupce zadané v **řazení** vlastnost **DataView**.</span><span class="sxs-lookup"><span data-stu-id="398ae-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="398ae-118">Následující příklad kódu ukazuje **najít** proti volané metody **DataView** s jedním sloupcem pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="398ae-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="398ae-119">Pokud vaše **řazení** vlastnost určuje více sloupců, musí předat objekt pole s hodnotami vyhledávání pro každý sloupec v pořadí zadaném **řazení** vlastnosti, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="398ae-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="398ae-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="398ae-120">See also</span></span>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="398ae-121">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="398ae-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="398ae-122">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="398ae-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
