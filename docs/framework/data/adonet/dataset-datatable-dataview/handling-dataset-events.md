---
title: Zpracování událostí datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: b2b71dac58838a826933af570934bf4bbb35e025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784605"
---
# <a name="handling-dataset-events"></a>Zpracování událostí datové sady
Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet>  
  
## <a name="the-mergefailed-event"></a>Událost MergeFailed  
 Nejčastěji používaná událost `DataSet` objektu je `MergeFailed`, která je vyvolána `DataSet` při konfliktu schématu objektů, které jsou sloučeny. K tomu dochází, pokud má cíl <xref:System.Data.DataRow> a zdroj stejnou hodnotu primárního klíče <xref:System.Data.DataSet.EnforceConstraints%2A> a vlastnost je nastavena na `true`. Například pokud jsou sloupce primárního klíče sloučené tabulky stejné mezi tabulkami v obou `DataSet` objektech, je vyvolána výjimka `MergeFailed` a událost je vyvolána. `MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> Objekt předaný události má vlastnost, která identifikuje konflikt ve schématu mezi dvěma `DataSet` objekty a vlastnost, která identifikuje název konfliktní tabulky. <xref:System.Data.MergeFailedEventArgs>  
  
 Následující fragment kódu ukazuje, jak přidat obslužnou rutinu události pro `MergeFailed` událost.  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>Inicializovaná událost  
 K události dochází poté, `DataSet` co konstruktor inicializuje novou instanci `DataSet`. <xref:System.Data.DataSet.Initialized>  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Vlastnost vrátí `false`, zda `DataSet` byla dokončena inicializace; v opačném případě vrátí. `true` Metoda, která zahájí inicializaci a `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> na `false`. <xref:System.Data.DataSet.BeginInit%2A> Metoda, která ukončí inicializaci `DataSet`, nastaví na `true`. <xref:System.Data.DataSet.EndInit%2A> Tyto metody jsou používány prostředím pro návrh sady Visual Studio k inicializaci `DataSet` , který je používán jinou komponentou. Nebudete je běžně používat ve svém kódu.  
  
## <a name="the-disposed-event"></a>Vyřazená událost  
 `DataSet`je odvozen z <xref:System.ComponentModel.MarshalByValueComponent> třídy, která zpřístupňuje <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> jak metodu <xref:System.ComponentModel.MarshalByValueComponent.Disposed> , tak událost. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události, která bude naslouchat vyřazené události na komponentě. Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událost `DataSet` , pokud chcete spustit kód při <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> volání metody. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Uvolňuje prostředky používané v <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
> Objekty `DataSet` a `DataTable` dědíz<xref:System.ComponentModel.MarshalByValueComponent> rozhraní a podporují ho pro vzdálenou komunikaci. <xref:System.Runtime.Serialization.ISerializable> Toto jsou jediné ADO.NET objekty, které je možné vzdáleně vymezit. Další informace najdete v tématu [Vzdálená komunikace rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).  
  
 Informace o dalších událostech, které jsou k dispozici při práci s a `DataSet`, naleznete v tématu [zpracování událostí DataTable](handling-datatable-events.md) a [zpracování událostí DataAdapter](../handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Ověřování dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))
- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
