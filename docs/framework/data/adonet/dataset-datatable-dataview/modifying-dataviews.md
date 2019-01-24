---
title: Úpravy zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: f892a371ed23a810f71ef5a51393de4145478c10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573241"
---
# <a name="modifying-dataviews"></a>Úpravy zobrazení dat
Můžete použít <xref:System.Data.DataView> Pokud chcete přidat, odstranit nebo upravit řádky dat v podkladové tabulce. Umožňuje používat **DataView** upravovat data v podkladové tabulce je řízen pomocí nastavení jedné z vlastností tři logické **DataView**. Tyto vlastnosti jsou <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, a <xref:System.Data.DataView.AllowDelete%2A>. Jsou nastaveny na **true** ve výchozím nastavení.  
  
 Pokud **vlastnost AllowNew** je **true**, můžete použít <xref:System.Data.DataView.AddNew%2A> metodu **DataView** k vytvoření nového <xref:System.Data.DataRowView>. Všimněte si, že nový řádek není ve skutečnosti přidán do základní <xref:System.Data.DataTable> až <xref:System.Data.DataRowView.EndEdit%2A> metodu **DataRowView** je volána. Pokud <xref:System.Data.DataRowView.CancelEdit%2A> metodu **DataRowView** je volána, nový řádek se zahodí. Upozorňujeme také, že můžete upravit pouze jeden **DataRowView** najednou. Při volání **AddNew** nebo **funkce BeginEdit** metodu **DataRowView** čeká na řádek existuje, **EndEdit –** je implicitně volán na čeká na řádek. Když **EndEdit –** je volána, změny se použijí k podkladovým **DataTable** a může být později potvrzeno nebo zamítnuto pomocí **metoda AcceptChanges** nebo  **RejectChanges** metody **DataTable**, **datovou sadu**, nebo **DataRow** objektu. Pokud **vlastnost AllowNew** je **false**, dojde k výjimce při volání **AddNew** metodu **DataRowView**.  
  
 Pokud **AllowEdit** je **true**, můžete upravit obsah **DataRow** prostřednictvím **DataRowView**. Můžete potvrdit změny podkladových řádků pomocí **DataRowView.EndEdit** nebo odmítnout změny pomocí **DataRowView.CancelEdit**. Mějte na paměti, že současně můžete upravit tento pouze jeden řádek. Při volání **AddNew** nebo **funkce BeginEdit** metody **DataRowView** čeká na řádek existuje, **EndEdit –** je implicitně volán na čeká na řádek. Když **EndEdit –** je volána, navrhované změny, které jsou umístěny v **aktuální** verze řádku základní **DataRow** a může být později potvrzené nebo odmítnuty pomocí **Metoda AcceptChanges** nebo **RejectChanges** metody **DataTable**, **datovou sadu**, nebo **DataRow** objekt. Pokud **AllowEdit** je **false**, je vyvolána výjimka, pokud se pokusíte změnit hodnotu **DataView**.  
  
 Pokud stávající **DataRowView** se právě upravuje, události základního **DataTable** stále, je vydána s navrhovaných změn. Všimněte si, že pokud zavoláte **EndEdit –** nebo **metodu CancelEdit** na základní **DataRow**, čekající změny budou použity nebo bez ohledu na to, zda bylo zrušeno  **EndEdit –** nebo **metodu CancelEdit** je volán na **DataRowView**.  
  
 Pokud **vlastnost AllowDelete** je **true**, můžete odstranit řádky z **DataView** pomocí **odstranit** metodu **DataView**  nebo **DataRowView** objektu a řádky budou odstraněny ze základního **DataTable**. Později můžete potvrdit nebo odmítnout odstraní pomocí **metoda AcceptChanges** nebo **RejectChanges** v uvedeném pořadí. Pokud **vlastnost AllowDelete** je **false**, dojde k výjimce při volání **odstranit** metodu **DataView** nebo  **DataRowView**.  
  
 Následující příklad kódu zakáže použití **DataView** k odstranění řádků a přidá nový řádek do podkladové tabulky pomocí **DataView**.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
