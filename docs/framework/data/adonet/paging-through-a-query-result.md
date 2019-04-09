---
title: Stránkování prostřednictvím výsledku dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 023efcc15d7080afc1583f4ad8984e152b86cf23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140319"
---
# <a name="paging-through-a-query-result"></a><span data-ttu-id="62854-102">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="62854-102">Paging Through a Query Result</span></span>
<span data-ttu-id="62854-103">Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožin data nebo stránky.</span><span class="sxs-lookup"><span data-stu-id="62854-103">Paging through a query result is the process of returning the results of a query in smaller subsets of data, or pages.</span></span> <span data-ttu-id="62854-104">To je běžný postup pro zobrazení výsledků pro uživatele v malé bloky snadno spravovat.</span><span class="sxs-lookup"><span data-stu-id="62854-104">This is a common practice for displaying results to a user in small, easy-to-manage chunks.</span></span>  
  
 <span data-ttu-id="62854-105">**DataAdapter** poskytuje zařízení pro vrácení pouze jednu stránku dat prostřednictvím přetížení **vyplnit** metody.</span><span class="sxs-lookup"><span data-stu-id="62854-105">The **DataAdapter** provides a facility for returning only a page of data, through overloads of the **Fill** method.</span></span> <span data-ttu-id="62854-106">Ale to nemusí být nejlepší volbou pro stránkování výsledků velký dotazu, protože i když **DataAdapter** vyplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky, které vrátí celý dotaz se stále používají.</span><span class="sxs-lookup"><span data-stu-id="62854-106">However, this might not be the best choice for paging through large query results because, although the **DataAdapter** fills the target <xref:System.Data.DataTable> or <xref:System.Data.DataSet> with only the requested records, the resources to return the entire query are still used.</span></span> <span data-ttu-id="62854-107">Pro vrácení stránky s dat ze zdroje dat bez použití prostředky pro vrácení celý dotaz, zadejte další kritéria dotazu, které omezení počtu řádků vrátí jenom ty povinné.</span><span class="sxs-lookup"><span data-stu-id="62854-107">To return a page of data from a data source without using the resources to return the entire query, specify additional criteria for your query that reduce the rows returned to only those required.</span></span>  
  
 <span data-ttu-id="62854-108">Použít **vyplnit** metodu pro návrat na stránku, zadejte **startRecord** parametr u prvního záznamu v stránku dat a **maxRecords** parametr po dobu záznamy na stránce data.</span><span class="sxs-lookup"><span data-stu-id="62854-108">To use the **Fill** method to return a page of data, specify a **startRecord** parameter, for the first record in the page of data, and a **maxRecords** parameter, for the number of records in the page of data.</span></span>  
  
 <span data-ttu-id="62854-109">Následující příklad kódu ukazuje, jak používat **vyplnit** metoda vrací první stránka výsledků dotazu, kde je velikost stránky je pět záznamů.</span><span class="sxs-lookup"><span data-stu-id="62854-109">The following code example shows how to use the **Fill** method to return the first page of a query result where the page size is five records.</span></span>  
  
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
  
 <span data-ttu-id="62854-110">V předchozím příkladu **datovou sadu** je pouze vyplněna pět záznamů, ale celou **objednávky** je vrácena tabulka.</span><span class="sxs-lookup"><span data-stu-id="62854-110">In the previous example, the **DataSet** is only filled with five records, but the entire **Orders** table is returned.</span></span> <span data-ttu-id="62854-111">K vyplnění **datovou sadu** tyto stejné pět záznamů, ale vracejí pouze pět záznamů, použijte horní a klauzule WHERE v příkazu jazyka SQL, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="62854-111">To fill the **DataSet** with those same five records, but only return five records, use the TOP and WHERE clauses in your SQL statement, as in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="62854-112">Všimněte si, že při procházení výsledky dotazu v tímto způsobem, musíte zachovat jedinečný identifikátor, který řadí řádků, abyste mohli předat jedinečné ID pro příkaz, který vrátí na další stránku záznamy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="62854-112">Note that, when paging through the query results in this way, you must preserve the unique identifier that orders the rows, in order to pass the unique ID to the command to return the next page of records, as shown in the following code example.</span></span>  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 <span data-ttu-id="62854-113">Se vraťte na další stránku záznamy pomocí přetížení **vyplnit** metodu, která přebírá **startRecord** a **maxRecords** parametry, zvyšovat index aktuální záznam podle velikost stránky a vyplnění tabulky.</span><span class="sxs-lookup"><span data-stu-id="62854-113">To return the next page of records using the overload of the **Fill** method that takes the **startRecord** and **maxRecords** parameters, increment the current record index by the page size and fill the table.</span></span> <span data-ttu-id="62854-114">Mějte na paměti, že databázový server vrátí výsledky celý dotaz i v případě, že pouze jednu stránku záznamů, které se přidá do **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="62854-114">Remember that the database server returns the entire query results even though only one page of records is added to the **DataSet**.</span></span> <span data-ttu-id="62854-115">V následujícím příkladu kódu jsou vymazány řádky tabulky předtím, než jsou vyplněny na další stránku.</span><span class="sxs-lookup"><span data-stu-id="62854-115">In the following code example, the table rows are cleared before they are filled with the next page of data.</span></span> <span data-ttu-id="62854-116">Můžete chtít zachovat určitý počet vrácených řádků v místní mezipaměti pro omezení cesty k databázi serveru.</span><span class="sxs-lookup"><span data-stu-id="62854-116">You might want to preserve a certain number of returned rows in a local cache to reduce trips to the database server.</span></span>  
  
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
  
 <span data-ttu-id="62854-117">Pokud chcete vrátit na další stránku záznamů bez nutnosti databázový server vrátí celý dotaz, zadejte omezující kritéria k příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="62854-117">To return the next page of records without having the database server return the entire query, specify restrictive criteria to the SELECT statement.</span></span> <span data-ttu-id="62854-118">Protože předchozí příklad zachovají vrátí poslední záznam, můžete použít v klauzuli WHERE, chcete-li určit výchozí bod pro dotaz, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="62854-118">Because the preceding example preserved the last record returned, you can use it in the WHERE clause to specify a starting point for the query, as shown in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62854-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62854-119">See also</span></span>

- [<span data-ttu-id="62854-120">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="62854-120">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="62854-121">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="62854-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
