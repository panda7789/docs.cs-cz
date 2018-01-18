---
title: "Úprava DataView"
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c31f256bb86f007a9d083370d116464607cde236
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="modifying-dataviews"></a>Úprava DataView
Můžete použít <xref:System.Data.DataView> Pokud chcete přidat, odstranit ani změnit řádky dat v podkladové tabulce. Možnost používat **DataView** změnit data v základní tabulce je řízeno nastavení jedné z vlastností tři logické **DataView**. Tyto vlastnosti jsou <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, a <xref:System.Data.DataView.AllowDelete%2A>. Jsou nastaveny na **true** ve výchozím nastavení.  
  
 Pokud **AllowNew** je **true**, můžete použít <xref:System.Data.DataView.AddNew%2A> metodu **DataView** pro vytvoření nového <xref:System.Data.DataRowView>. Všimněte si, že nový řádek není ve skutečnosti přidán do základní <xref:System.Data.DataTable> dokud <xref:System.Data.DataRowView.EndEdit%2A> metodu **DataRowView** je volána. Pokud <xref:System.Data.DataRowView.CancelEdit%2A> metodu **DataRowView** je volána, budou zahozeny nový řádek. Všimněte si také, že můžete upravit pouze jeden **DataRowView** najednou. Při volání **AddNew** nebo **BeginEdit** metodu **DataRowView** čekající řádek existuje, **EndEdit –** se implicitně volá na čeká na řádek. Při **EndEdit –** je volána, změny se použijí na odpovídající **DataTable** a může být později potvrzené nebo odmítnuté, pomocí **metoda AcceptChanges** nebo  **RejectChanges** metody **DataTable**, **datovou sadu**, nebo **DataRow** objektu. Pokud **AllowNew** je **false**, je vyvolána výjimka při volání **AddNew** metodu **DataRowView**.  
  
 Pokud **AllowEdit** je **true**, můžete upravit obsah **DataRow** prostřednictvím **DataRowView**. Můžete potvrdit změny základní řádek pomocí **DataRowView.EndEdit** nebo odmítnout změny pomocí **DataRowView.CancelEdit**. Všimněte si, že pouze jeden řádek se dá upravit v čase. Když zavoláte **AddNew** nebo **BeginEdit** metody **DataRowView** čekající řádek existuje, **EndEdit –** se implicitně volá na čeká na řádek. Když **EndEdit –** je volána, navrhované změny, které jsou umístěny v **aktuální** verze řádku základní **DataRow** a může být později potvrzené nebo odmítnuté, pomocí  **Metoda AcceptChanges** nebo **RejectChanges** metody **DataTable**, **datovou sadu**, nebo **DataRow** objekt. Pokud **AllowEdit** je **false**, je vyvolána výjimka, pokud se pokusíte změnit hodnotu v **DataView**.  
  
 Pokud stávající **DataRowView** upravována, události základní **DataTable** bude stále vyvolána s navrhované změny. Všimněte si, že při volání **EndEdit –** nebo **CancelEdit** na základní **DataRow**, čekající změny budou použity nebo došlo ke zrušení bez ohledu na to, jestli se  **EndEdit –** nebo **CancelEdit** se volá na **DataRowView**.  
  
 Pokud **vlastnost AllowDelete** je **true**, můžete odstranit řádky z **DataView** pomocí **odstranit** metodu **zobrazení dat**  nebo **DataRowView** objekt a řádky budou odstraněny ze základní **DataTable**. Později můžete potvrdit nebo odmítnout odstranění pomocí **metoda AcceptChanges** nebo **RejectChanges** v uvedeném pořadí. Pokud **vlastnost AllowDelete** je **false**, je vyvolána výjimka při volání **odstranit** metodu **DataView** nebo  **DataRowView**.  
  
 Následující příklad kódu zakáže použití **DataView** k odstranění řádků a přidá nový řádek na základní tabulku pomocí **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
