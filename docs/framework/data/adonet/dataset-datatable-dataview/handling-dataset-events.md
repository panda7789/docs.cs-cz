---
title: Zpracování událostí datové sady
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: aea9fc2caae675b77a8aad730869adb00f593baf
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="handling-dataset-events"></a><span data-ttu-id="ab082-102">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="ab082-102">Handling DataSet Events</span></span>
<span data-ttu-id="ab082-103"><xref:System.Data.DataSet> Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>.</span><span class="sxs-lookup"><span data-stu-id="ab082-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="ab082-104">Událost MergeFailed</span><span class="sxs-lookup"><span data-stu-id="ab082-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="ab082-105">Nejčastěji používá události `DataSet` objekt `MergeFailed`, která se vyvolá, když schéma `DataSet` slučování objekty jsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="ab082-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="ab082-106">K tomu dojde, pokud zdrojové a cílové <xref:System.Data.DataRow> mají stejnou hodnotu primárního klíče a <xref:System.Data.DataSet.EnforceConstraints%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="ab082-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="ab082-107">Například pokud slučování primární klíčové sloupce tabulky identická mezi tabulkami ve dvou `DataSet` objekty, je vyvolána výjimka a `MergeFailed` událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="ab082-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="ab082-108"><xref:System.Data.MergeFailedEventArgs> Byl předán objekt `MergeFailed` událost mít <xref:System.Data.MergeFailedEventArgs.Conflict%2A> vlastnost, která identifikuje konflikt ve schématu mezi těmito dvěma `DataSet` objekty a <xref:System.Data.MergeFailedEventArgs.Table%2A> vlastnost, která identifikuje název tabulky v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="ab082-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="ab082-109">Následující fragment kódu ukazuje, jak přidat obslužné rutiny události pro `MergeFailed` událostí.</span><span class="sxs-lookup"><span data-stu-id="ab082-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="ab082-110">Inicializovanou událost</span><span class="sxs-lookup"><span data-stu-id="ab082-110">The Initialized Event</span></span>  
 <span data-ttu-id="ab082-111"><xref:System.Data.DataSet.Initialized> Události dojde po `DataSet` konstruktor inicializuje novou instanci třídy `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="ab082-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="ab082-112"><xref:System.Data.DataSet.IsInitialized%2A> Vlastnost vrátí `true` Pokud `DataSet` dokončení inicializace; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="ab082-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="ab082-113"><xref:System.Data.DataSet.BeginInit%2A> Metodu, která začíná inicializace `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="ab082-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="ab082-114"><xref:System.Data.DataSet.EndInit%2A> Metoda, což ukončí inicializace `DataSet`, nastaví na `true`.</span><span class="sxs-lookup"><span data-stu-id="ab082-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="ab082-115">Tyto metody jsou používány vývojového prostředí sady Visual Studio k chybě při inicializaci `DataSet` který se používá jinou součástí.</span><span class="sxs-lookup"><span data-stu-id="ab082-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="ab082-116">Nebudete používat běžně je ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="ab082-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="ab082-117">Uvolněné událostí</span><span class="sxs-lookup"><span data-stu-id="ab082-117">The Disposed Event</span></span>  
 <span data-ttu-id="ab082-118">`DataSet` je odvozený od <xref:System.ComponentModel.MarshalByValueComponent> třídy, která zpřístupňuje jak <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda a <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událostí.</span><span class="sxs-lookup"><span data-stu-id="ab082-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="ab082-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události pro naslouchání na uvolněné událostí na komponentu.</span><span class="sxs-lookup"><span data-stu-id="ab082-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="ab082-120">Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> události `DataSet` Pokud chcete provést kódu, kdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="ab082-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="ab082-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> uvolní prostředky používané <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="ab082-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab082-122">`DataSet` a `DataTable` objekty dědí <xref:System.ComponentModel.MarshalByValueComponent> a podporovat <xref:System.Runtime.Serialization.ISerializable> rozhraní pro vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="ab082-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="ab082-123">Jedná se o pouze ADO.NET objekty, které se dají používat vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="ab082-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="ab082-124">Další informace najdete v tématu [vzdálených objektů](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span><span class="sxs-lookup"><span data-stu-id="ab082-124">For more information, see [Remote Objects](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58).</span></span>  
  
 <span data-ttu-id="ab082-125">Informace o dalších událostí, které jsou k dispozici při práci se službou `DataSet`, najdete v části [zpracování události DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) a [zpracování události DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="ab082-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) and [Handling DataAdapter Events](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab082-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab082-126">See Also</span></span>  
 [<span data-ttu-id="ab082-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ab082-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ab082-128">Ověřování dat</span><span class="sxs-lookup"><span data-stu-id="ab082-128">Validating Data</span></span>](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [<span data-ttu-id="ab082-129">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ab082-129">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="ab082-130">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ab082-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
