---
title: Hledání řádků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 2ff2b6b6d00c854d07f36d37986268a388c7f31b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203713"
---
# <a name="finding-rows"></a><span data-ttu-id="d9c09-102">Hledání řádků</span><span class="sxs-lookup"><span data-stu-id="d9c09-102">Finding Rows</span></span>
<span data-ttu-id="d9c09-103">Můžete vyhledat řádky podle jejich hodnot klíče řazení pomocí <xref:System.Data.DataView.Find%2A> metod <xref:System.Data.DataView>a <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="d9c09-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="d9c09-104">Rozlišuje velká a malá písmena vyhledávacích hodnot v metodách **find** a **FindRows** je určena vlastností **CaseSensitive** podkladového <xref:System.Data.DataTable>výrazu.</span><span class="sxs-lookup"><span data-stu-id="d9c09-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d9c09-105">Aby bylo možné vrátit výsledek, musí hodnoty hledání odpovídat existujícím hodnotám klíčového řazení v celém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="d9c09-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="d9c09-106">Metoda **find** vrátí celé číslo s indexem <xref:System.Data.DataRowView> , který odpovídá kritériím hledání.</span><span class="sxs-lookup"><span data-stu-id="d9c09-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="d9c09-107">Pokud kritériím vyhledávání odpovídá více než jeden řádek, vrátí se pouze index prvního odpovídajícího **DataRowViewu** .</span><span class="sxs-lookup"><span data-stu-id="d9c09-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="d9c09-108">Nejsou-li nalezeny žádné shody, funkce **find** vrátí hodnotu-1.</span><span class="sxs-lookup"><span data-stu-id="d9c09-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="d9c09-109">Chcete-li vrátit výsledky hledání, které odpovídají více řádkům, použijte metodu **FindRows** .</span><span class="sxs-lookup"><span data-stu-id="d9c09-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="d9c09-110">**FindRows** funguje stejně jako metoda **find** s tím rozdílem, že vrátí pole **DataRowView** , které odkazuje na všechny odpovídající řádky v objektu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="d9c09-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="d9c09-111">Pokud se nenajde žádná shoda, pole **DataRowView** bude prázdné.</span><span class="sxs-lookup"><span data-stu-id="d9c09-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="d9c09-112">Chcete-li použít metody **find** nebo **FindRows** , je nutné zadat pořadí řazení buď nastavením **ApplyDefaultSort** na **hodnotu true** nebo pomocí vlastnosti **Sort** .</span><span class="sxs-lookup"><span data-stu-id="d9c09-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="d9c09-113">Pokud není zadáno žádné pořadí řazení, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d9c09-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="d9c09-114">Metody **find** a **FindRows** přebírají pole hodnot jako vstup, jejichž délka odpovídá počtu sloupců v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="d9c09-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="d9c09-115">V případě řazení v jednom sloupci můžete předat jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d9c09-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="d9c09-116">Pro pořadí řazení obsahující více sloupců předáte pole objektů.</span><span class="sxs-lookup"><span data-stu-id="d9c09-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="d9c09-117">Všimněte si, že pro řazení více sloupců musí hodnoty v poli objektu odpovídat pořadí sloupců, které jsou zadány ve vlastnosti **Sort** objektu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="d9c09-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="d9c09-118">Následující příklad kódu ukazuje metodu **find** , která je volána proti zobrazení **DataView** s jedním sloupcem řazení.</span><span class="sxs-lookup"><span data-stu-id="d9c09-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="d9c09-119">Pokud vlastnost **Sort** určuje více sloupců, musíte předat pole objektu s hodnotami hledání pro každý sloupec v pořadí určeném vlastností **Sort** , jak je uvedeno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d9c09-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9c09-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9c09-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="d9c09-121">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="d9c09-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="d9c09-122">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d9c09-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
