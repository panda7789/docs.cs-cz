---
title: Úpravy zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 0b2bfd1b0490572e78c8ce365491a8d48db87684
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204574"
---
# <a name="modifying-dataviews"></a>Úpravy zobrazení dat
Pomocí <xref:System.Data.DataView> můžete přidat, odstranit nebo upravit řádky dat v podkladové tabulce. Možnost použít zobrazení **DataView** ke změně dat v podkladové tabulce je ovládána nastavením jedné ze tří logických vlastností objektu **DataView**. Tyto vlastnosti jsou <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>a <xref:System.Data.DataView.AllowDelete%2A>. Ve výchozím nastavení jsou nastaveny na **hodnotu true** .  
  
 Pokud má AllowNew **hodnotu true**, <xref:System.Data.DataView.AddNew%2A> můžete k vytvoření nové <xref:System.Data.DataRowView>použít metodu zobrazení **DataView** . Všimněte si, že nový řádek není ve skutečnosti přidán do <xref:System.Data.DataTable> podkladu <xref:System.Data.DataRowView.EndEdit%2A> , dokud nebude volána metoda **DataRowView** . Pokud je volána MetodaDataRowView,novýřádekje<xref:System.Data.DataRowView.CancelEdit%2A> zahozen. Všimněte si také, že v jednu chvíli můžete upravovat jenom jeden **DataRowView** . Pokud zavoláte metodu **AddNew** nebo **metody BeginEdit** **DataRowView** , zatímco existuje řádek, který čeká na vyřízení, **metodu EndEdit volat** se implicitně volá na nevyřízeném řádku. Při volání **metodu EndEdit volat** jsou změny použity v podkladovém **objektu DataTable** a lze je později potvrdit nebo odmítat pomocí metod **AcceptChanges** nebo **RejectChanges** **objektu DataTable**, **datové sady**nebo  **Objekt DataRow** Pokud je AllowNew **false**, je vyvolána výjimka, pokud zavoláte metodu **AddNew** objektu **DataRowView**.  
  
 Pokud má AllowEdit **hodnotu true**, můžete upravit obsah objektu **DataRow** prostřednictvím rozhraní **DataRowView**. Změny v podkladovém řádku můžete potvrdit pomocí **DataRowView. metodu EndEdit volat** nebo změny zamítnout pomocí **DataRowView. CancelEdit**. Všimněte si, že v jednu chvíli lze upravovat pouze jeden řádek. Pokud zavoláte metody **AddNew** nebo **metody BeginEdit** **DataRowView** , zatímco existuje řádek, který čeká na vyřízení, **metodu EndEdit volat** je implicitně voláno na nevyřízeném řádku. Když se zavolá **metodu EndEdit volat** , navrhované změny se umístí do **aktuální** verze řádku podkladového objektu **DataRow** a dají se později potvrdit nebo odmítat pomocí metod **AcceptChanges nebo RejectChanges. DataTable**, **DataSet**nebo objekt **DataRow** . Pokud je AllowEdit **false**, je vyvolána výjimka, pokud se pokusíte změnit hodnotu v zobrazení **DataView**.  
  
 Pokud je upravován existující **DataRowView** , budou události podkladového **objektu DataTable** stále vyvolány navrhovanými změnami. Všimněte si, že pokud **voláte metodu EndEdit volat** nebo **CancelEdit** v podkladovém objektu **DataRow**, budou se nedokončené změny použít nebo zrušeny bez ohledu na to, zda je na **DataRowView**voláno **metodu EndEdit volat** nebo **CancelEdit** .  
  
 Pokud má AllowDelete **hodnotu true**, můžete odstranit řádky z objektu **DataView** pomocí metody **Delete** objektu **DataView** nebo **DataRowView** a řádky jsou odstraněny z podkladového objektu **DataTable**. Odstranění později můžete potvrdit nebo odmítnout pomocí příkazu **AcceptChanges** nebo **RejectChanges** v uvedeném pořadí. Pokud je AllowDelete **false**, je vyvolána výjimka, pokud zavoláte metodu **Delete** objektu **DataView** nebo **DataRowView**.  
  
 Následující příklad kódu deaktivuje použití objektu **DataView** k odstranění řádků a přidá nový řádek do podkladové tabulky pomocí objektu **DataView**.  
  
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
- [Zobrazení dat](dataviews.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
