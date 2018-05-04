---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 9e67aef2a39a04adfdcc036c008aa80c9151c14b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="handling-dataview-events"></a>Zpracování událostí zobrazení dat
Můžete použít <xref:System.Data.DataView.ListChanged> události <xref:System.Data.DataView> k určení, zda byl aktualizován zobrazení. Aktualizace, které vyvolání události zahrnují přidání, odstranění nebo úprava řádek v podkladové tabulce; Přidání nebo odstranění sloupce schématu základní tabulky; a změnu ve vztahu nadřazené nebo podřízené. **ListChanged** událostí taky upozorní, zda seznam řádků prohlížíte významně změnil z důvodu aplikace nové pořadí řazení nebo filtru.  
  
 **ListChanged** implementuje událostí **ListChangedEventHandler** delegovat z <xref:System.ComponentModel> obor názvů a přijímá jako vstup <xref:System.ComponentModel.ListChangedEventArgs> objektu. Můžete určit, jaký typ změny došlo k použití <xref:System.ComponentModel.ListChangedType> hodnota výčtu v **ListChangedType** vlastnost **ListChangedEventArgs** objektu. Změny, které zahrnují přidání, odstranění nebo přesunutí řádků, nový index řádku přidané nebo přesunutý a předchozí index odstraněné řádku lze přistupovat pomocí **NewIndex** vlastnost **ListChangedEventArgs** objektu. V případě přesunutý řádek, předchozí index přesunutý řádku lze přistupovat pomocí **OldIndex** vlastnost **ListChangedEventArgs** objektu.  
  
 **DataViewManager** taky zpřístupňuje **ListChanged** události pro upozornění, pokud tabulka byl přidán nebo odebrán, nebo pokud ke změně k **vztahů** kolekce základní **datovou sadu**.  
  
 Následující příklad kódu ukazuje, jak přidat **ListChanged** obslužné rutiny události.  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new   
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,   
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataView>  
 <xref:System.ComponentModel.ListChangedEventHandler>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
