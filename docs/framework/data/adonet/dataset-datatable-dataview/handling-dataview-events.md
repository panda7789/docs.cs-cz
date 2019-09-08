---
title: Zpracování událostí zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: c36c68b0375e7d03aac36de7d02b2c9579ea9316
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784597"
---
# <a name="handling-dataview-events"></a>Zpracování událostí zobrazení dat
Můžete použít <xref:System.Data.DataView.ListChanged> událost <xref:System.Data.DataView> k určení, zda bylo zobrazení aktualizováno. Aktualizace, které vyvolávají událost, zahrnují přidání, odstranění nebo úpravu řádku v podkladové tabulce; Přidání nebo odstranění sloupce ve schématu podkladové tabulky; a změna v relaci nadřazeného nebo podřízeného vztahu. Událost **ListChanged** vás také upozorní, pokud se seznam zobrazených řádků významně změnil v důsledku použití nového pořadí řazení nebo filtru.  
  
 Událost **ListChanged** implementuje <xref:System.ComponentModel> delegáta **ListChangedEventHandler** <xref:System.ComponentModel.ListChangedEventArgs> oboru názvů a přijímá jako vstup objekt. Můžete určit, jaký typ změny došlo, pomocí <xref:System.ComponentModel.ListChangedType> hodnoty výčtu ve vlastnosti **ListChangedType** objektu **ListChangedEventArgs** . Pro změny, které zahrnují přidání, odstranění nebo přesunutí řádků, je k novému indexu přidaných nebo přesunutých řádků a k předchozímu indexu odstraněného řádku možné přistupovat pomocí vlastnosti **NewIndex** objektu **ListChangedEventArgs** . V případě přesunutého řádku je k předchozímu indexu přesunutého řádku možné přistupovat pomocí vlastnosti **OldIndex** objektu **ListChangedEventArgs** .  
  
 Objekt **DataViewManager** také zpřístupňuje událost **ListChanged** , která vás upozorní, pokud byla tabulka přidána nebo odebrána, nebo pokud byla provedena změna v kolekci **Relations** podkladové **datové sady**.  
  
 Následující příklad kódu ukazuje, jak přidat obslužnou rutinu události **ListChanged** .  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)
