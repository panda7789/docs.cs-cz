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
# <a name="paging-through-a-query-result"></a>Stránkování prostřednictvím výsledku dotazu
Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožinech dat nebo stránek. Toto je běžný postup pro zobrazení výsledků uživateli v malých, snadno spravovat bloky.  
  
 **DataAdapter** poskytuje zařízení pro vrácení pouze stránku dat, prostřednictvím přetížení **Fill** metody. To však nemusí být nejlepší volbou pro stránkování prostřednictvím velkých výsledků dotazu, protože přestože **DataAdapter** vyplňuje cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky pro vrácení celého dotazu jsou stále používány. Chcete-li vrátit stránku dat ze zdroje dat bez použití prostředků k vrácení celého dotazu, zadejte další kritéria pro dotaz, která snižují řádky vrácené pouze na ty, které jsou požadovány.  
  
 Chcete-li použít metodu **Fill** k vrácení stránky dat, zadejte parametr **startRecord** pro první záznam na stránce dat a parametr **maxRecords** pro počet záznamů na stránce dat.  
  
 Následující příklad kódu ukazuje, jak použít **fill** metodu vrátit první stránku výsledku dotazu, kde velikost stránky je pět záznamů.  
  
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
  
 V předchozím příkladu **dataset** je vyplněna pouze pět záznamů, ale je vrácena celá tabulka **Objednávky.** Chcete-li vyplnit **DataSet** s těmito pěti záznamů, ale vrátí pouze pět záznamů, použijte TOP a WHERE klauzule v příkazu SQL, jako v následujícím příkladu kódu.  
  
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
  
 Všimněte si, že při stránkování prostřednictvím výsledků dotazu tímto způsobem je nutné zachovat jedinečný identifikátor, který objednávky řádků, aby bylo možné předat jedinečné ID příkazu vrátit další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Chcete-li vrátit další stránku záznamů pomocí přetížení **Fill** metoda, která přebírá **startRecord** a **maxRecords** parametry, převáděj aktuální index záznamu o velikost stránky a vyplňte tabulku. Nezapomeňte, že databázový server vrátí výsledky celého dotazu, i když je do **datové sady**přidána pouze jedna stránka záznamů . V následujícím příkladu kódu jsou řádky tabulky vymazány před vyplněním další stránky dat. Můžete chtít zachovat určitý počet vrácených řádků v místní mezipaměti snížit cesty na databázový server.  
  
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
  
 Chcete-li vrátit další stránku záznamů bez nutnosti, aby databázový server vrátil celý dotaz, zadejte omezující kritéria do příkazu SELECT. Vzhledem k tomu, že předchozí příklad zachoval poslední vrácený záznam, můžete jej použít v klauzuli WHERE k určení výchozího bodu pro dotaz, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Přehled ADO.NET](ado-net-overview.md)
