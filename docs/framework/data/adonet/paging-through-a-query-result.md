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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 83e8241fed71ec4dd0ea32f97b02373f3a1d56bb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="paging-through-a-query-result"></a>Stránkování prostřednictvím výsledku dotazu
Stránkování prostřednictvím výsledku dotazu je proces vrácení výsledků dotazu v menších podmnožin dat nebo stránky. Toto je běžnou praxí při zobrazování výsledků uživateli na malé bloky snadno spravovat.  
  
 **DataAdapter** poskytuje budovy pro vrácení pouze jednu stránku dat prostřednictvím přetížení **vyplnění** metoda. Ale nemusí to být nejlepší volbou pro stránkování výsledků velký dotazu, protože i když **DataAdapter** doplní cíl <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> se pouze požadované záznamy, prostředky se vrátíte celý dotaz se stále používají. Pokud chcete vrátit stránku dat ze zdroje dat bez použití prostředky vrátit celý dotaz, zadejte další kritéria pro svůj dotaz, která snižují vrátí jenom ty požadované řádky.  
  
 Použít **vyplnění** metoda vrátí stránku dat, zadejte **startRecord** parametr pro první záznam na stránce dat a **maxRecords** parametr pro počet záznamy na stránce data.  
  
 Následující příklad kódu ukazuje, jak používat **vyplnění** metoda vrátí první stránka výsledků dotazu, kde je velikost stránky pět záznamů.  
  
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
  
 V předchozím příkladu **datovou sadu** pouze vyplněno pět záznamů, ale celý **objednávky** tabulce se vrátí. K vyplnění **datovou sadu** s tyto stejného pět záznamů, ale pouze návratový pět záznamů, použijte horní a klauzule WHERE v příkazu SQL, jako v následujícím příkladu kódu.  
  
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
  
 Všimněte si, že při procházení výsledky dotazu tímto způsobem, musí zachovat jedinečný identifikátor, který řadí řádky, aby bylo možné předat jedinečné ID příkazu a vrátit na další stránku záznamů, jak je znázorněno v následujícím příkladu kódu.  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 Vrátit na další stránku záznamů pomocí přetížení **vyplnění** metody, která přijímá **startRecord** a **maxRecords** parametry, zvýší aktuální index záznam podle velikost stránky a vyplňte v tabulce. Mějte na paměti, že databázový server vrátí výsledky celý dotaz, i když pouze jednu stránku záznamů je přidat do **datovou sadu**. V následujícím příkladu kódu jsou vymazány řádky tabulky, které předtím, než jsou vyplněny na další stránku data. Můžete chtít zachovat počet vrácených řádků v místní mezipaměti pro omezení cest k serveru databáze.  
  
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
  
 Pokud chcete vrátit na další stránku záznamů bez nutnosti databázový server vrátí celý dotaz, zadejte omezující kritéria pro příkaz SELECT. Protože v předchozím příkladu zachovají poslední záznam vrácen, můžete použít v klauzuli WHERE zadat počáteční bod pro dotaz, jak je znázorněno v následujícím příkladu kódu.  
  
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
