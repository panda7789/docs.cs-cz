---
title: Zpracování událostí datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 88ff0be43099758c076216e963d139b945936ba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652940"
---
# <a name="handling-dataset-events"></a>Zpracování událostí datové sady
<xref:System.Data.DataSet> Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>MergeFailed události  
 Nejběžněji používané událost `DataSet` objekt `MergeFailed`, které se vyvolá, když schéma `DataSet` objekty, které jsou slučovány, je v konfliktu. K tomu dojde, pokud zdrojové a cílové <xref:System.Data.DataRow> mají stejnou hodnotu primárního klíče a <xref:System.Data.DataSet.EnforceConstraints%2A> je nastavena na `true`. Pokud se sloučí sloupce primárního klíče tabulky jsou například stejné mezi tabulkami ve dvou `DataSet` objektů, dojde k výjimce a `MergeFailed` událost se vyvolá. <xref:System.Data.MergeFailedEventArgs> Předán objekt `MergeFailed` událost mít <xref:System.Data.MergeFailedEventArgs.Conflict%2A> vlastnost, která identifikuje konflikt ve schématu mezi těmito dvěma `DataSet` objekty a <xref:System.Data.MergeFailedEventArgs.Table%2A> vlastnost, která identifikuje název tabulky v konfliktu.  
  
 Následující fragment kódu ukazuje, jak přidat obslužnou rutinu události pro `MergeFailed` událostí.  
  
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
  
## <a name="the-initialized-event"></a>Inicializovanou událost  
 <xref:System.Data.DataSet.Initialized> Po dojde k události `DataSet` konstruktor inicializuje novou instanci třídy `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Vrátí vlastnost `true` Pokud `DataSet` dokončení inicializace; v opačném případě vrátí `false`. <xref:System.Data.DataSet.BeginInit%2A> Metodu, která začíná inicializace `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> k `false`. <xref:System.Data.DataSet.EndInit%2A> Metoda, která končí v inicializaci `DataSet`, nastaví na `true`. Tyto metody jsou používány návrhové prostředí sady Visual Studio k inicializaci `DataSet` , který je používán jinou komponentou. Že služby nebudete používat běžně ve vašem kódu.  
  
## <a name="the-disposed-event"></a>Uvolněné události  
 `DataSet` je odvozen z <xref:System.ComponentModel.MarshalByValueComponent> třídu, která zpřístupňuje jak <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda a <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událostí. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události tak, aby naslouchala na vyřazený událost na komponentu. Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> události `DataSet` Pokud budete chtít spustit kód při <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda je volána. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> uvolní prostředky využívané třídou <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` a `DataTable` objekty dědit z <xref:System.ComponentModel.MarshalByValueComponent> a podporu <xref:System.Runtime.Serialization.ISerializable> rozhraní pro vzdálenou komunikaci. Jedná se pouze objekty ADO.NET, které lze používat vzdáleně. Další informace najdete v tématu [vzdálené objekty](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Informace o dalších událostí, které jsou k dispozici při práci s `DataSet`, naleznete v tématu [zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) a [zpracování událostí adaptéru dat](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také:
- [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Ověřování dat](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
- [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
