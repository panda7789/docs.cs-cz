---
title: Stránkování prostřednictvím výsledku dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 2e7fb97e5c0cb42deff43c411f47e8d30e2257ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149385"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="f5668-102">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="f5668-102">Paging Through a Query Result</span></span>
<span data-ttu-id="f5668-103">Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožinech dat nebo stránek.</span><span class="sxs-lookup"><span data-stu-id="f5668-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="f5668-104">Toto je běžný postup pro zobrazení výsledků uživateli v malých, snadno spravovat bloky.</span><span class="sxs-lookup"><span data-stu-id="f5668-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="f5668-105">**DataAdapter** poskytuje zařízení pro vrácení pouze stránku dat, prostřednictvím přetížení **Fill** metody.</span><span class="sxs-lookup"><span data-stu-id="f5668-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="f5668-106">To však nemusí být nejlepší volbou pro stránkování prostřednictvím velkých výsledků dotazu, protože přestože **DataAdapter** vyplňuje cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky pro vrácení celého dotazu jsou stále používány.</span><span class="sxs-lookup"><span data-stu-id="f5668-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="f5668-107">Chcete-li vrátit stránku dat ze zdroje dat bez použití prostředků k vrácení celého dotazu, zadejte další kritéria pro dotaz, která snižují řádky vrácené pouze na ty, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="f5668-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="f5668-108">Chcete-li použít metodu **Fill** k vrácení stránky dat, zadejte parametr **startRecord** pro první záznam na stránce dat a parametr **maxRecords** pro počet záznamů na stránce dat.</span><span class="sxs-lookup"><span data-stu-id="f5668-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="f5668-109">Následující příklad kódu ukazuje, jak použít **fill** metodu vrátit první stránku výsledku dotazu, kde velikost stránky je pět záznamů.</span><span class="sxs-lookup"><span data-stu-id="f5668-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="f5668-110">V předchozím příkladu **dataset** je vyplněna pouze pět záznamů, ale je vrácena celá tabulka **Objednávky.**</span><span class="sxs-lookup"><span data-stu-id="f5668-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="f5668-111">Chcete-li vyplnit **DataSet** s těmito pěti záznamů, ale vrátí pouze pět záznamů, použijte TOP a WHERE klauzule v příkazu SQL, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f5668-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 <span data-ttu-id="f5668-112">Všimněte si, že při stránkování prostřednictvím výsledků dotazu tímto způsobem je nutné zachovat jedinečný identifikátor, který objednávky řádků, aby bylo možné předat jedinečné ID příkazu vrátit další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f5668-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="f5668-113">Chcete-li vrátit další stránku záznamů pomocí přetížení **Fill** metoda, která přebírá **startRecord** a **maxRecords** parametry, převáděj aktuální index záznamu o velikost stránky a vyplňte tabulku.</span><span class="sxs-lookup"><span data-stu-id="f5668-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="f5668-114">Nezapomeňte, že databázový server vrátí výsledky celého dotazu, i když je do **datové sady**přidána pouze jedna stránka záznamů .</span><span class="sxs-lookup"><span data-stu-id="f5668-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="f5668-115">V následujícím příkladu kódu jsou řádky tabulky vymazány před vyplněním další stránky dat.</span><span class="sxs-lookup"><span data-stu-id="f5668-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="f5668-116">Můžete chtít zachovat určitý počet vrácených řádků v místní mezipaměti snížit cesty na databázový server.</span><span class="sxs-lookup"><span data-stu-id="f5668-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 <span data-ttu-id="f5668-117">Chcete-li vrátit další stránku záznamů bez nutnosti, aby databázový server vrátil celý dotaz, zadejte omezující kritéria do příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="f5668-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="f5668-118">Vzhledem k tomu, že předchozí příklad zachoval poslední vrácený záznam, můžete jej použít v klauzuli WHERE k určení výchozího bodu pro dotaz, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="f5668-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5668-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5668-119">See also</span></span>

- [<span data-ttu-id="f5668-120">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="f5668-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="f5668-121">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f5668-121">ADO.NET Overview</span></span>](ado-net-overview.md)
