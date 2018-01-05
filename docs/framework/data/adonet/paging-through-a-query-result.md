---
title: "Stránkování prostřednictvím výsledku dotazu"
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
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 506458eab146614f505a5558cd3535f06aecb83c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="b2656-102">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="b2656-102">Paging Through a Query Result</span></span>
<span data-ttu-id="b2656-103">Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožin dat nebo stránky.</span><span class="sxs-lookup"><span data-stu-id="b2656-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="b2656-104">Toto je běžnou praxí při zobrazování výsledků uživateli na malé bloky snadno spravovat.</span><span class="sxs-lookup"><span data-stu-id="b2656-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="b2656-105">**DataAdapter** poskytuje budovy pro vrácení pouze jednu stránku dat prostřednictvím přetížení **vyplnění** metoda.</span><span class="sxs-lookup"><span data-stu-id="b2656-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="b2656-106">Ale nemusí to být nejlepší volbou pro stránkování výsledků velký dotazu, protože i když **DataAdapter** doplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> se pouze požadované záznamy, prostředky se vrátíte celý dotaz se stále používají.</span><span class="sxs-lookup"><span data-stu-id="b2656-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="b2656-107">Pokud chcete vrátit stránku dat ze zdroje dat bez použití prostředky vrátit celý dotaz, zadejte další kritéria pro svůj dotaz, která snižují vrátí jenom ty požadované řádky.</span><span class="sxs-lookup"><span data-stu-id="b2656-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="b2656-108">Použít **vyplnění** metoda vrátí stránku dat, zadejte **startRecord** parametr pro první záznam na stránce dat a **maxRecords** parametr pro počet záznamy na stránce data.</span><span class="sxs-lookup"><span data-stu-id="b2656-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="b2656-109">Následující příklad kódu ukazuje, jak používat **vyplnění** metoda vrátí první stránka výsledků dotazu, kde je velikost stránky pět záznamů.</span><span class="sxs-lookup"><span data-stu-id="b2656-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="b2656-110">V předchozím příkladu **datovou sadu** pouze vyplněno pět záznamů, ale celý **objednávky** tabulce se vrátí.</span><span class="sxs-lookup"><span data-stu-id="b2656-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="b2656-111">K vyplnění **datovou sadu** s tyto stejného pět záznamů, ale pouze návratový pět záznamů, použijte horní a klauzule WHERE v příkazu SQL, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b2656-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="b2656-112">Všimněte si, že při procházení výsledky dotazu tímto způsobem, musí zachovat jedinečný identifikátor, který řadí řádky, aby bylo možné předat jedinečné ID příkazu a vrátit na další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b2656-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="b2656-113">Vrátit na další stránku záznamů pomocí přetížení **vyplnění** metody, která přijímá **startRecord** a **maxRecords** parametry, zvýší aktuální index záznam podle velikost stránky a vyplňte v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b2656-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="b2656-114">Mějte na paměti, že databázový server vrátí výsledky celý dotaz, i když pouze jednu stránku záznamů je přidat do **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="b2656-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="b2656-115">V následujícím příkladu kódu jsou vymazány řádky tabulky, které předtím, než jsou vyplněny na další stránku data.</span><span class="sxs-lookup"><span data-stu-id="b2656-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="b2656-116">Můžete chtít zachovat počet vrácených řádků v místní mezipaměti pro omezení cest k serveru databáze.</span><span class="sxs-lookup"><span data-stu-id="b2656-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="b2656-117">Pokud chcete vrátit na další stránku záznamů bez nutnosti databázový server vrátí celý dotaz, zadejte omezující kritéria pro příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="b2656-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="b2656-118">Protože v předchozím příkladu zachovají poslední záznam vrácen, můžete použít v klauzuli WHERE zadat počáteční bod pro dotaz, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b2656-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2656-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2656-119">See Also</span></span>  
 [<span data-ttu-id="b2656-120">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b2656-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b2656-121">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b2656-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
