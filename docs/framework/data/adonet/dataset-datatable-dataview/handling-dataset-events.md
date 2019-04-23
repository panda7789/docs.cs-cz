---
title: Zpracování událostí datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 5e1de3effcae5700aa25f5dbb84f2dec3a0b20f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195278"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="e46b8-102">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="e46b8-102">Handling DataSet Events</span></span>
<span data-ttu-id="e46b8-103"><xref:System.Data.DataSet> Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="e46b8-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="e46b8-104">MergeFailed události</span><span class="sxs-lookup"><span data-stu-id="e46b8-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="e46b8-105">Nejběžněji používané událost `DataSet` objekt `MergeFailed`, které se vyvolá, když schéma `DataSet` objekty, které jsou slučovány, je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="e46b8-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="e46b8-106">K tomu dojde, pokud zdrojové a cílové <xref:System.Data.DataRow> mají stejnou hodnotu primárního klíče a <xref:System.Data.DataSet.EnforceConstraints%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="e46b8-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="e46b8-107">Pokud se sloučí sloupce primárního klíče tabulky jsou například stejné mezi tabulkami ve dvou `DataSet` objektů, dojde k výjimce a `MergeFailed` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="e46b8-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="e46b8-108"><xref:System.Data.MergeFailedEventArgs> Předán objekt `MergeFailed` událost mít <xref:System.Data.MergeFailedEventArgs.Conflict%2A> vlastnost, která identifikuje konflikt ve schématu mezi těmito dvěma `DataSet` objekty a <xref:System.Data.MergeFailedEventArgs.Table%2A> vlastnost, která identifikuje název tabulky v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="e46b8-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="e46b8-109">Následující fragment kódu ukazuje, jak přidat obslužnou rutinu události pro `MergeFailed` událostí.</span><span class="sxs-lookup"><span data-stu-id="e46b8-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="e46b8-110">Inicializovanou událost</span><span class="sxs-lookup"><span data-stu-id="e46b8-110">The Initialized Event</span></span>  
 <span data-ttu-id="e46b8-111"><xref:System.Data.DataSet.Initialized> Po dojde k události `DataSet` konstruktor inicializuje novou instanci třídy `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e46b8-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="e46b8-112"><xref:System.Data.DataSet.IsInitialized%2A> Vrátí vlastnost `true` Pokud `DataSet` dokončení inicializace; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="e46b8-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="e46b8-113"><xref:System.Data.DataSet.BeginInit%2A> Metodu, která začíná inicializace `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="e46b8-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="e46b8-114"><xref:System.Data.DataSet.EndInit%2A> Metoda, která končí v inicializaci `DataSet`, nastaví na `true`.</span><span class="sxs-lookup"><span data-stu-id="e46b8-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="e46b8-115">Tyto metody jsou používány návrhové prostředí sady Visual Studio k inicializaci `DataSet` , který je používán jinou komponentou.</span><span class="sxs-lookup"><span data-stu-id="e46b8-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="e46b8-116">Že služby nebudete používat běžně ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e46b8-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="e46b8-117">Uvolněné události</span><span class="sxs-lookup"><span data-stu-id="e46b8-117">The Disposed Event</span></span>  
 <span data-ttu-id="e46b8-118">`DataSet` je odvozen z <xref:System.ComponentModel.MarshalByValueComponent> třídu, která zpřístupňuje jak <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda a <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událostí.</span><span class="sxs-lookup"><span data-stu-id="e46b8-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="e46b8-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události tak, aby naslouchala na vyřazený událost na komponentu.</span><span class="sxs-lookup"><span data-stu-id="e46b8-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="e46b8-120">Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> události `DataSet` Pokud budete chtít spustit kód při <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="e46b8-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="e46b8-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> uvolní prostředky využívané třídou <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="e46b8-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e46b8-122">`DataSet` a `DataTable` objekty dědit z <xref:System.ComponentModel.MarshalByValueComponent> a podporu <xref:System.Runtime.Serialization.ISerializable> rozhraní pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="e46b8-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="e46b8-123">Jedná se pouze objekty ADO.NET, které lze používat vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="e46b8-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="e46b8-124">Další informace najdete v tématu [vzdálené komunikace .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e46b8-124">For more information, see [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="e46b8-125">Informace o dalších událostí, které jsou k dispozici při práci s `DataSet`, naleznete v tématu [zpracování událostí datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) a [zpracování událostí adaptéru dat](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="e46b8-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46b8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e46b8-126">See also</span></span>

- [<span data-ttu-id="e46b8-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="e46b8-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- <span data-ttu-id="e46b8-128">[Ověřování dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="e46b8-128">[Validating Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="e46b8-129">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e46b8-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="e46b8-130">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="e46b8-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
