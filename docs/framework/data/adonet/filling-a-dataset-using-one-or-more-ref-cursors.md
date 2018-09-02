---
title: Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 99863e79-5b00-467e-a105-4ffa42de3ff7
ms.openlocfilehash: 78e1a2ce73be1e83284a1d8caa657ff645262e09
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420669"
---
# <a name="filling-a-dataset-using-one-or-more-ref-cursors"></a><span data-ttu-id="ff70a-102">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="ff70a-102">Filling a DataSet Using One or More REF CURSORs</span></span>
<span data-ttu-id="ff70a-103">Tento příklad Microsoft Visual Basicu provede PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a doplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="ff70a-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff70a-104">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff70a-104">See Also</span></span>  
 [<span data-ttu-id="ff70a-105">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="ff70a-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="ff70a-106">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ff70a-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
