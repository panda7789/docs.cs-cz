---
title: Stránkování prostřednictvím výsledku dotazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 5d86095586af273f62980fcf8ddf10804b1cfa5a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406807"
---
# <a name="paging-through-a-query-result"></a>Stránkování prostřednictvím výsledku dotazu
Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožin data nebo stránky. To je běžný postup pro zobrazení výsledků pro uživatele v malé bloky snadno spravovat.  
  
 **DataAdapter** poskytuje zařízení pro vrácení pouze jednu stránku dat prostřednictvím přetížení **vyplnit** metody. Ale to nemusí být nejlepší volbou pro stránkování výsledků velký dotazu, protože i když **DataAdapter** vyplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> pouze požadované záznamy, prostředky, které vrátí celý dotaz se stále používají. Pro vrácení stránky s dat ze zdroje dat bez použití prostředky pro vrácení celý dotaz, zadejte další kritéria dotazu, které omezení počtu řádků vrátí jenom ty povinné.  
  
 Použít **vyplnit** metodu pro návrat na stránku, zadejte **startRecord** parametr u prvního záznamu v stránku dat a **maxRecords** parametr po dobu záznamy na stránce data.  
  
 Následující příklad kódu ukazuje, jak používat **vyplnit** metoda vrací první stránka výsledků dotazu, kde je velikost stránky je pět záznamů.  
  
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
  
 V předchozím příkladu **datovou sadu** je pouze vyplněna pět záznamů, ale celou **objednávky** je vrácena tabulka. K vyplnění **datovou sadu** tyto stejné pět záznamů, ale vracejí pouze pět záznamů, použijte horní a klauzule WHERE v příkazu jazyka SQL, jako v následujícím příkladu kódu.  
  
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
  
 Všimněte si, že při procházení výsledky dotazu v tímto způsobem, musíte zachovat jedinečný identifikátor, který řadí řádků, abyste mohli předat jedinečné ID pro příkaz, který vrátí na další stránku záznamy, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Se vraťte na další stránku záznamy pomocí přetížení **vyplnit** metodu, která přebírá **startRecord** a **maxRecords** parametry, zvyšovat index aktuální záznam podle velikost stránky a vyplnění tabulky. Mějte na paměti, že databázový server vrátí výsledky celý dotaz i v případě, že pouze jednu stránku záznamů, které se přidá do **datovou sadu**. V následujícím příkladu kódu jsou vymazány řádky tabulky předtím, než jsou vyplněny na další stránku. Můžete chtít zachovat určitý počet vrácených řádků v místní mezipaměti pro omezení cesty k databázi serveru.  
  
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
  
 Pokud chcete vrátit na další stránku záznamů bez nutnosti databázový server vrátí celý dotaz, zadejte omezující kritéria k příkazu SELECT. Protože předchozí příklad zachovají vrátí poslední záznam, můžete použít v klauzuli WHERE, chcete-li určit výchozí bod pro dotaz, jak je znázorněno v následujícím příkladu kódu.  
  
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
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
