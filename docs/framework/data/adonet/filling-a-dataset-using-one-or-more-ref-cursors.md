---
title: "Naplnění datové sady pomocí jednoho nebo více REF kurzory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 56284888f681434635f8ea320f4ab99b12854fc5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a><span data-ttu-id="69f9f-102">Naplnění datové sady pomocí jednoho nebo více REF kurzory</span><span class="sxs-lookup"><span data-stu-id="69f9f-102">Filling a DataSet Using One or More REF CURSORs</span></span>
<span data-ttu-id="69f9f-103">Tento příklad Microsoft Visual Basicu provede PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a výplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="69f9f-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
    "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Dim ds As New DataSet()  
    Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter( _  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
       ParameterDirection.Output  
  
    Dim da As New OracleDataAdapter(cmd)  
    da.TableMappings.Add("Table", "Emp")  
    da.TableMappings.Add("Table1", "Dept")  
    da.Fill(ds)  
  
    ds.Relations.Add("EmpDept", ds.Tables("Dept").Columns("Deptno"), _  
      ds.Tables("Emp").Columns("Deptno"), False)  
  
    DataGrid1.DataSource = ds.Tables("Dept")  
  End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="69f9f-104">Viz také</span><span class="sxs-lookup"><span data-stu-id="69f9f-104">See Also</span></span>  
 [<span data-ttu-id="69f9f-105">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="69f9f-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="69f9f-106">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="69f9f-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
