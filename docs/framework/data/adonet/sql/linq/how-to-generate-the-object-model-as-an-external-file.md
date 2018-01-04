---
title: "Postupy: generování objektový Model jako externí soubor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5ffcc1c4664955de9a5dd2f7848290c273efbea1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Postupy: generování objektový Model jako externí soubor
Jako alternativu k mapování na základě atributů můžete pomocí nástroje příkazového řádku na SQLMetal vygenerovat objektový model jako externí soubor XML. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Pomocí externího souboru XML mapování snížit zbytečné soubory do vašeho kódu. Můžete také změnit chování změnou externího souboru bez nutnosti rekompilace binární soubory aplikace. Další informace najdete v tématu [externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nepodporuje vzniku souboru externí mapování.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří soubor externí mapování z ukázková databáze Northwind.  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Příklad  
 Následující výňatek ze souboru externí mapování zobrazuje v ukázková databáze Northwind mapování pro tabulku zákazníků. Tato výňatek ze byl vygenerován spuštěním na SQLMetal s **/map** možnost.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Externí mapování](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Postupy: Generování objektového modelu v jazyce Visual Basic nebo C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
