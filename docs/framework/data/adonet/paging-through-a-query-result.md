---
title: Stránkování prostřednictvím výsledku dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 1dbaa159314bf7bb05ff75287f601f619834fd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794622"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="417aa-102">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="417aa-102">Paging Through a Query Result</span></span>
<span data-ttu-id="417aa-103">Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožinách dat nebo na stránkách.</span><span class="sxs-lookup"><span data-stu-id="417aa-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="417aa-104">To je běžný postup pro zobrazení výsledků pro uživatele v malých, snadno ovladatelném bloku.</span><span class="sxs-lookup"><span data-stu-id="417aa-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="417aa-105">Objekt **DataAdapter** poskytuje zařízení pro vrácení pouze stránky dat prostřednictvím přetížení metody **Fill** .</span><span class="sxs-lookup"><span data-stu-id="417aa-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="417aa-106">To však nemusí být nejlepší volbou pro stránkování prostřednictvím velkých výsledků dotazu, protože ačkoliv modul **DataAdapter** vyplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky, které mají vracet celý dotaz, jsou stále používány. .</span><span class="sxs-lookup"><span data-stu-id="417aa-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="417aa-107">Chcete-li vrátit stránku dat ze zdroje dat bez použití prostředků, které vrátí celý dotaz, zadejte další kritéria pro dotaz, který zmenší počet vrácených řádků pouze na ty, které jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="417aa-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="417aa-108">Chcete-li použít metodu **Fill** k vrácení stránky dat, zadejte parametr **startRecord** pro první záznam na stránce dat a parametr **MaxRecords** pro počet záznamů na stránce dat.</span><span class="sxs-lookup"><span data-stu-id="417aa-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="417aa-109">Následující příklad kódu ukazuje, jak použít metodu **Fill** k vrácení první stránky výsledku dotazu, kde je velikost stránky pět záznamů.</span><span class="sxs-lookup"><span data-stu-id="417aa-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="417aa-110">V předchozím příkladu je **datová sada** vyplněna pouze pěti záznamy, ale celá tabulka **Orders** je vrácena.</span><span class="sxs-lookup"><span data-stu-id="417aa-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="417aa-111">Chcete-li **datovou sadu** vyplnit pomocí těchto pěti záznamů, ale vrátit pouze pět záznamů, použijte klauzuli TOP a WHERE v příkazu jazyka SQL, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="417aa-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="417aa-112">Všimněte si, že pokud je výsledkem stránkování přes dotaz, je nutné zachovat jedinečný identifikátor, který řádky seřadí, aby bylo možné předat jedinečné ID do příkazu, který vrátí další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="417aa-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="417aa-113">Chcete-li vrátit další stránku záznamů pomocí přetížení metody **Fill** , která přijímá parametry **startRecord** a **MaxRecords** , zvyšte aktuální index záznamu velikostí stránky a vyplňte tabulku.</span><span class="sxs-lookup"><span data-stu-id="417aa-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="417aa-114">Pamatujte, že databázový server vrátí výsledky celého dotazu, i když do **datové sady**se přidá jenom jedna stránka záznamů.</span><span class="sxs-lookup"><span data-stu-id="417aa-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="417aa-115">V následujícím příkladu kódu jsou před vyplněním další stránky dat vymazány řádky tabulky.</span><span class="sxs-lookup"><span data-stu-id="417aa-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="417aa-116">Je možné, že budete chtít zachovat určitý počet vrácených řádků v místní mezipaměti pro omezení cest k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="417aa-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="417aa-117">Chcete-li vrátit další stránku záznamů, aniž by měl databázový server vracet celý dotaz, zadejte omezující kritéria do příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="417aa-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="417aa-118">Vzhledem k tomu, že předchozí příklad zachovává poslední vrácenou položku, můžete ji použít v klauzuli WHERE k určení počátečního bodu pro dotaz, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="417aa-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="417aa-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="417aa-119">See also</span></span>

- [<span data-ttu-id="417aa-120">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="417aa-120">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="417aa-121">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="417aa-121">ADO.NET Overview</span></span>](ado-net-overview.md)
