---
title: Načítání dat z více REF kurzory pomocí připojení OracleDataReader
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: ae33786cda956d3e01e6a904369a1f1b114d0b6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356170"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="bc6a6-102">Načítání dat z více REF kurzory pomocí připojení OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="bc6a6-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>
<span data-ttu-id="bc6a6-103">Tento příklad Microsoft Visual Basicu provede PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a přečte hodnoty pomocí <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="bc6a6-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click( _  
  ByVal sender As Object, ByVal e As System.EventArgs)  _  
  Handles Button1.Click  
  
  Dim connString As New String( _  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter(_  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
    While (rdr.Read())  
        REM do something with the values from the EMP table   
    End While  
  
    rdr.NextResult()  
    While (rdr.Read())  
        REM do something with the values from the DEPT table   
    End While  
    rdr.Close()  
  End Using  
End Sub   
```  
  
## <a name="see-also"></a><span data-ttu-id="bc6a6-104">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc6a6-104">See Also</span></span>  
 [<span data-ttu-id="bc6a6-105">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="bc6a6-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="bc6a6-106">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="bc6a6-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
