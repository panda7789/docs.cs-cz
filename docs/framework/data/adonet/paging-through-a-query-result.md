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
# <a name="paging-through-a-query-result"></a>Stránkování prostřednictvím výsledku dotazu
Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožinách dat nebo na stránkách. To je běžný postup pro zobrazení výsledků pro uživatele v malých, snadno ovladatelném bloku.  
  
 Objekt **DataAdapter** poskytuje zařízení pro vrácení pouze stránky dat prostřednictvím přetížení metody **Fill** . To však nemusí být nejlepší volbou pro stránkování prostřednictvím velkých výsledků dotazu, protože ačkoliv modul **DataAdapter** vyplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky, které mají vracet celý dotaz, jsou stále používány. . Chcete-li vrátit stránku dat ze zdroje dat bez použití prostředků, které vrátí celý dotaz, zadejte další kritéria pro dotaz, který zmenší počet vrácených řádků pouze na ty, které jsou požadovány.  
  
 Chcete-li použít metodu **Fill** k vrácení stránky dat, zadejte parametr **startRecord** pro první záznam na stránce dat a parametr **MaxRecords** pro počet záznamů na stránce dat.  
  
 Následující příklad kódu ukazuje, jak použít metodu **Fill** k vrácení první stránky výsledku dotazu, kde je velikost stránky pět záznamů.  
  
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
  
 V předchozím příkladu je **datová sada** vyplněna pouze pěti záznamy, ale celá tabulka **Orders** je vrácena. Chcete-li **datovou sadu** vyplnit pomocí těchto pěti záznamů, ale vrátit pouze pět záznamů, použijte klauzuli TOP a WHERE v příkazu jazyka SQL, jako v následujícím příkladu kódu.  
  
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
  
 Všimněte si, že pokud je výsledkem stránkování přes dotaz, je nutné zachovat jedinečný identifikátor, který řádky seřadí, aby bylo možné předat jedinečné ID do příkazu, který vrátí další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Chcete-li vrátit další stránku záznamů pomocí přetížení metody **Fill** , která přijímá parametry **startRecord** a **MaxRecords** , zvyšte aktuální index záznamu velikostí stránky a vyplňte tabulku. Pamatujte, že databázový server vrátí výsledky celého dotazu, i když do **datové sady**se přidá jenom jedna stránka záznamů. V následujícím příkladu kódu jsou před vyplněním další stránky dat vymazány řádky tabulky. Je možné, že budete chtít zachovat určitý počet vrácených řádků v místní mezipaměti pro omezení cest k databázovému serveru.  
  
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
  
 Chcete-li vrátit další stránku záznamů, aniž by měl databázový server vracet celý dotaz, zadejte omezující kritéria do příkazu SELECT. Vzhledem k tomu, že předchozí příklad zachovává poslední vrácenou položku, můžete ji použít v klauzuli WHERE k určení počátečního bodu pro dotaz, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Přehled ADO.NET](ado-net-overview.md)
