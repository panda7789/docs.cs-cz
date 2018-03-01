---
title: "Parametry KURZORU REF v připojení OracleDataReader"
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
ms.assetid: 801dff0f-2508-45aa-9416-f45d6887740c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3cfee7568925c4898fd2c1480ebd4d9323bfc876
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="ref-cursor-parameters-in-an-oracledatareader"></a><span data-ttu-id="f8475-102">Parametry KURZORU REF v připojení OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="f8475-102">REF CURSOR Parameters in an OracleDataReader</span></span>
<span data-ttu-id="f8475-103">Tento příklad Microsoft Visual Basicu provede PL/SQL uložené procedury, která vrátí parametr REF kurzor a přečte hodnotu jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="f8475-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click(ByVal sender As Object, _  
  ByVal e As System.EventArgs) Handles Button1.Click  
  
  Dim connString As New String(_  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_ONE_CURSOR"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter(  
      "N_EMPNO", OracleType.Number)).Value = 7369  
    cmd.Parameters.Add(New OracleParameter(  
      "IO_CURSOR", OracleType.Cursor)).Direction = ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader()  
    While (rdr.Read())  
        REM do something with the values  
    End While  
  
    rdr.Close()  
  End Using  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8475-104">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8475-104">See Also</span></span>  
 [<span data-ttu-id="f8475-105">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="f8475-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="f8475-106">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="f8475-106">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
