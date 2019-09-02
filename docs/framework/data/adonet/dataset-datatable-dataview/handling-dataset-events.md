---
title: Zpracování událostí datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 88f35d90f02b44b88f4bb7c6fac6a94a09afe81a
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204849"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="8ef55-102">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="8ef55-102">Handling DataSet Events</span></span>
<span data-ttu-id="8ef55-103">Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="8ef55-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="8ef55-104">Událost MergeFailed</span><span class="sxs-lookup"><span data-stu-id="8ef55-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="8ef55-105">Nejčastěji používaná událost `DataSet` objektu je `MergeFailed`, která je vyvolána `DataSet` při konfliktu schématu objektů, které jsou sloučeny.</span><span class="sxs-lookup"><span data-stu-id="8ef55-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="8ef55-106">K tomu dochází, pokud má cíl <xref:System.Data.DataRow> a zdroj stejnou hodnotu primárního klíče <xref:System.Data.DataSet.EnforceConstraints%2A> a vlastnost je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="8ef55-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="8ef55-107">Například pokud jsou sloupce primárního klíče sloučené tabulky stejné mezi tabulkami v obou `DataSet` objektech, je vyvolána výjimka `MergeFailed` a událost je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8ef55-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="8ef55-108">`MergeFailed` <xref:System.Data.MergeFailedEventArgs.Conflict%2A> <xref:System.Data.MergeFailedEventArgs.Table%2A> Objekt předaný události má vlastnost, která identifikuje konflikt ve schématu mezi dvěma `DataSet` objekty a vlastnost, která identifikuje název konfliktní tabulky. <xref:System.Data.MergeFailedEventArgs></span><span class="sxs-lookup"><span data-stu-id="8ef55-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="8ef55-109">Následující fragment kódu ukazuje, jak přidat obslužnou rutinu události pro `MergeFailed` událost.</span><span class="sxs-lookup"><span data-stu-id="8ef55-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
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
  
## <a name="the-initialized-event"></a><span data-ttu-id="8ef55-110">Inicializovaná událost</span><span class="sxs-lookup"><span data-stu-id="8ef55-110">The Initialized Event</span></span>  
 <span data-ttu-id="8ef55-111">K události dochází poté, `DataSet` co konstruktor inicializuje novou instanci `DataSet`. <xref:System.Data.DataSet.Initialized></span><span class="sxs-lookup"><span data-stu-id="8ef55-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="8ef55-112"><xref:System.Data.DataSet.IsInitialized%2A> Vlastnost vrátí `false`, zda `DataSet` byla dokončena inicializace; v opačném případě vrátí. `true`</span><span class="sxs-lookup"><span data-stu-id="8ef55-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="8ef55-113">Metoda, která zahájí inicializaci a `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> na `false`. <xref:System.Data.DataSet.BeginInit%2A></span><span class="sxs-lookup"><span data-stu-id="8ef55-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="8ef55-114">Metoda, která ukončí inicializaci `DataSet`, nastaví na `true`. <xref:System.Data.DataSet.EndInit%2A></span><span class="sxs-lookup"><span data-stu-id="8ef55-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="8ef55-115">Tyto metody jsou používány prostředím pro návrh sady Visual Studio k inicializaci `DataSet` , který je používán jinou komponentou.</span><span class="sxs-lookup"><span data-stu-id="8ef55-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="8ef55-116">Nebudete je běžně používat ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="8ef55-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="8ef55-117">Vyřazená událost</span><span class="sxs-lookup"><span data-stu-id="8ef55-117">The Disposed Event</span></span>  
 <span data-ttu-id="8ef55-118">`DataSet`je odvozen z <xref:System.ComponentModel.MarshalByValueComponent> třídy, která zpřístupňuje <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> jak metodu <xref:System.ComponentModel.MarshalByValueComponent.Disposed> , tak událost.</span><span class="sxs-lookup"><span data-stu-id="8ef55-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="8ef55-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události, která bude naslouchat vyřazené události na komponentě.</span><span class="sxs-lookup"><span data-stu-id="8ef55-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="8ef55-120">Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událost `DataSet` , pokud chcete spustit kód při <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="8ef55-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="8ef55-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>Uvolňuje prostředky používané v <xref:System.ComponentModel.MarshalByValueComponent>.</span><span class="sxs-lookup"><span data-stu-id="8ef55-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ef55-122">Objekty `DataSet` a `DataTable` dědíz<xref:System.ComponentModel.MarshalByValueComponent> rozhraní a podporují ho pro vzdálenou komunikaci. <xref:System.Runtime.Serialization.ISerializable></span><span class="sxs-lookup"><span data-stu-id="8ef55-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="8ef55-123">Toto jsou jediné ADO.NET objekty, které je možné vzdáleně vymezit.</span><span class="sxs-lookup"><span data-stu-id="8ef55-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="8ef55-124">Další informace najdete v tématu [Vzdálená komunikace rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8ef55-124">For more information, see [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="8ef55-125">Informace o dalších událostech, které jsou k dispozici při práci s a `DataSet`, naleznete v tématu [zpracování událostí DataTable](handling-datatable-events.md) a [zpracování událostí DataAdapter](../handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="8ef55-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef55-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ef55-126">See also</span></span>

- [<span data-ttu-id="8ef55-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="8ef55-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="8ef55-128">[Ověřování dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8ef55-128">[Validating Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="8ef55-129">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8ef55-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="8ef55-130">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8ef55-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
