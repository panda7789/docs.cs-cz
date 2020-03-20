---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: b625fad846c4c6cf008843bff1f6b0eabe0e1de4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151101"
---
# <a name="handling-dataview-events"></a>Zpracování událostí zobrazení dat
Událost <xref:System.Data.DataView.ListChanged> zobrazení můžete použít <xref:System.Data.DataView> k určení, zda bylo zobrazení aktualizováno. Aktualizace, které vyvolávají událost patří přidání, odstranění nebo úprava řádku v podkladové tabulce; přidání nebo odstranění sloupce do schématu podkladové tabulky; a změna v nadřazeném nebo podřízeném vztahu. Událost **ListChanged** vás také upozorní, pokud se seznam řádků, které prohlížíte, výrazně změnil z důvodu použití nového pořadí řazení nebo filtru.  
  
 Událost **ListChanged** implementuje delegáta oboru <xref:System.ComponentModel> názvů **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> a bere jako vstupní objekt. Můžete určit, jaký typ změny <xref:System.ComponentModel.ListChangedType> došlo pomocí hodnoty výčtu v **ListChangedType** vlastnost **í ListChangedEventArgs** objektu. Pro změny, které zahrnují přidání, odstranění nebo přesunutí řádků, nový index přidaného nebo přesunutého řádku a předchozí index odstraněného řádku lze přistupovat pomocí **Vlastnost NewIndex** objektu **ListChangedEventArgs.** V případě přesunutého řádku lze získat přístup k předchozímu indexu přesunutého řádku pomocí vlastnosti **OldIndex** objektu **ListChangedEventArgs.**  
  
 **DataViewManager** také zveřejňuje **ListChanged** událost upozornit, pokud tabulka byla přidána nebo odebrána, nebo pokud byla provedena změna **kolekce vztahy** podkladové **DataSet**.  
  
 Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události **ListChanged.**  
  
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

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)
