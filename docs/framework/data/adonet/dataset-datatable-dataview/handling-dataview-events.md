---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2f30a578c5233e8b86a165dd220efd45348c5042
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401261"
---
# <a name="handling-dataview-events"></a>Zpracování událostí zobrazení dat
Můžete použít <xref:System.Data.DataView.ListChanged> událost <xref:System.Data.DataView> k určení, jestli má aktualizované zobrazení. Aktualizace, které vyvolávají události zahrnují přidání, odstranění nebo úprava řádků v podkladové tabulce; Přidání nebo odstranění sloupce do schématu podkladové tabulce. a změna v nadřazené nebo podřízené relace. **ListChanged** události také vás upozorní, pokud seznam řádků se vám zobrazuje významně změnil z důvodu použití nového pořadí řazení nebo filtru.  
  
 **ListChanged** implementuje událostí **ListChangedEventHandler** delegáta z <xref:System.ComponentModel> obor názvů a přijímá jako vstup <xref:System.ComponentModel.ListChangedEventArgs> objektu. Můžete určit, jaký typ změn došlo k použití <xref:System.ComponentModel.ListChangedType> hodnota výčtu v **ListChangedType** vlastnost **ListChangedEventArgs** objektu. Změny, které zahrnují přidání, odstranění nebo Přesun řádků, nový index řádku přidané nebo přesunut a předchozí index odstraněném řádku lze přistupovat pomocí **NewIndex** vlastnost **ListChangedEventArgs** objektu. V případě řádku přesunutý předchozí index řádku přesunutý lze přistupovat pomocí **OldIndex** vlastnost **ListChangedEventArgs** objektu.  
  
 **Objekt DataViewManager** taky zpřístupňuje **ListChanged** události, které vás upozorní, pokud tabulky byly přidány nebo odebrány nebo pokud byla provedena změna **vztahy** kolekce základní **datovou sadu**.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
