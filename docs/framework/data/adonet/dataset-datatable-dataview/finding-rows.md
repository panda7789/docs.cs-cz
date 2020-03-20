---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151140"
---
# <a name="finding-rows"></a><span data-ttu-id="1e4d8-102">Hledání řádků</span><span class="sxs-lookup"><span data-stu-id="1e4d8-102">Finding Rows</span></span>
<span data-ttu-id="1e4d8-103">Řádky můžete vyhledávat podle jejich hodnot klíče <xref:System.Data.DataView.Find%2A> řazení <xref:System.Data.DataView.FindRows%2A> pomocí <xref:System.Data.DataView>metody a .</span><span class="sxs-lookup"><span data-stu-id="1e4d8-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="1e4d8-104">Rozlišování malých a velkých písmen vyhledávacích hodnot v find **a** **findrows** metody je určena **CaseSensitive** vlastnost podkladové <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1e4d8-105">Vyhledávací hodnoty musí odpovídat existující hodnoty klíče řazení v plném rozsahu, aby se vrátil výsledek.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="1e4d8-106">Find **Find** Metoda vrátí celé číslo s indexem, <xref:System.Data.DataRowView> který odpovídá kritériím vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="1e4d8-107">Pokud více než jeden řádek odpovídá kritériím hledání, je vrácen pouze index první odpovídající **DataRowView.**</span><span class="sxs-lookup"><span data-stu-id="1e4d8-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="1e4d8-108">Pokud nejsou nalezeny žádné shody, **Find** vrátí -1.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="1e4d8-109">Chcete-li vrátit výsledky hledání, které odpovídají více řádkům, použijte metodu **FindRows.**</span><span class="sxs-lookup"><span data-stu-id="1e4d8-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="1e4d8-110">**FindRows** funguje stejně jako **Find** metoda, s tím rozdílem, že vrátí **DataRowView** pole, které odkazuje na všechny odpovídající řádky v **DataView**.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="1e4d8-111">Pokud nejsou nalezeny žádné shody, pole **DataRowView** bude prázdné.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="1e4d8-112">Chcete-li použít metody **Find** nebo **FindRows,** musíte zadat pořadí řazení buď nastavením **ApplyDefaultSort** na **true,** nebo pomocí vlastnosti **Seřadit.**</span><span class="sxs-lookup"><span data-stu-id="1e4d8-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="1e4d8-113">Pokud není zadáno žádné pořadí řazení, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1e4d8-114">**Find** a **FindRows** Metody trvat pole hodnot jako vstup, jehož délka odpovídá počtu sloupců v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="1e4d8-115">V případě řazení na jednom sloupci můžete předat jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="1e4d8-116">U pořadí řazení obsahujících více sloupců předáte pole objektů.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="1e4d8-117">Všimněte si, že pro řazení na více sloupcích musí hodnoty v poli objektů odpovídat pořadí sloupců zadaných ve vlastnosti **Sort** **zobrazení DataView**.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="1e4d8-118">Následující příklad kódu ukazuje **Find** metoda volána proti **DataView** s pořadí řazení jednoho sloupce.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="1e4d8-119">Pokud vaše vlastnost **Sort** určuje více sloupců, musíte předat pole objektů s vyhledávacími hodnotami pro každý sloupec v pořadí určeném vlastností **Seřadit,** jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="1e4d8-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e4d8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e4d8-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="1e4d8-121">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="1e4d8-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="1e4d8-122">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1e4d8-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
