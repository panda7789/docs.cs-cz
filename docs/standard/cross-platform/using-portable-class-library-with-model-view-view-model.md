---
title: Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b48dc67e18411d82f03d29ab244d57575d6d720
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835782"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="117eb-102">Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)</span><span class="sxs-lookup"><span data-stu-id="117eb-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="117eb-103">Můžete použít rozhraní .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementovat vzor Model-View-View Model (MVVM) a sdílet sestavení napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="117eb-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="117eb-104">MVVM je vzorek aplikace, který izoluje uživatelského rozhraní ze základní obchodní logiku.</span><span class="sxs-lookup"><span data-stu-id="117eb-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="117eb-105">Můžete implementovat modelu a zobrazení tříd modelu v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu v sadě Visual Studio 2012 a pak vytvořte zobrazení, která jsou přizpůsobená pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="117eb-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="117eb-106">Tento přístup umožňuje zapisovat data model a obchodní logiky pouze jednou a použít tento kód v rozhraní .NET Framework, Silverlight, Windows Phone a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="117eb-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 <span data-ttu-id="117eb-107">![Přenosné s modelem MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="117eb-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>

 <span data-ttu-id="117eb-108">Toto téma neposkytuje obecné informace o vzoru MVVM.</span><span class="sxs-lookup"><span data-stu-id="117eb-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="117eb-109">Nabízí informace o tom, jak používat [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] implementovat MVVM.</span><span class="sxs-lookup"><span data-stu-id="117eb-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="117eb-110">Další informace o MVVM, najdete v článku [MVVM rychlém startu pomocí knihovny 5.0 modulu Prism pro WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="117eb-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="117eb-111">Třídy, které podporují MVVM</span><span class="sxs-lookup"><span data-stu-id="117eb-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="117eb-112">Pokud cílíte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight nebo Windows Phone 7.5 pro vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, jsou k dispozici pro implementaci vzoru MVVM následující třídy:</span><span class="sxs-lookup"><span data-stu-id="117eb-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>

-   <span data-ttu-id="117eb-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Třída</span><span class="sxs-lookup"><span data-stu-id="117eb-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

-   <span data-ttu-id="117eb-123">Všechny třídy v <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> obor názvů</span><span class="sxs-lookup"><span data-stu-id="117eb-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="117eb-124">Implementace MVVM</span><span class="sxs-lookup"><span data-stu-id="117eb-124">Implementing MVVM</span></span>
 <span data-ttu-id="117eb-125">K implementaci MVVM, obvykle vytvoříte model a model v zobrazení [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, protože [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] nepřenositelný projekt nemůže odkazovat na projekt.</span><span class="sxs-lookup"><span data-stu-id="117eb-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="117eb-126">Model a model zobrazení může být ve stejném projektu nebo v samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="117eb-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="117eb-127">Pokud používáte samostatné projekty, přidejte odkaz z projektu zobrazení modelu do projektu s modelem.</span><span class="sxs-lookup"><span data-stu-id="117eb-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="117eb-128">Po kompilaci modelu a zobrazit projekty modelu, můžete odkazovat na tato sestavení v aplikaci, která obsahuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="117eb-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="117eb-129">Pokud zobrazení pracuje pouze s model zobrazení, stačí odkazovat na sestavení, který obsahuje model zobrazení.</span><span class="sxs-lookup"><span data-stu-id="117eb-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="117eb-130">Model</span><span class="sxs-lookup"><span data-stu-id="117eb-130">Model</span></span>
 <span data-ttu-id="117eb-131">Následující příklad ukazuje zjednodušený model třídu, která může být umístěn v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="117eb-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="117eb-132">Následující příklad ukazuje jednoduchý způsob, jak naplnit, načíst a aktualizovat data v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="117eb-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="117eb-133">V reálné aplikaci byste načíst data ze zdroje, jako je například služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="117eb-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="117eb-134">Model zobrazení</span><span class="sxs-lookup"><span data-stu-id="117eb-134">View Model</span></span>
 <span data-ttu-id="117eb-135">Základní třída pro zobrazení modely se často přidá při implementaci vzoru MVVM.</span><span class="sxs-lookup"><span data-stu-id="117eb-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="117eb-136">Následující příklad ukazuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="117eb-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="117eb-137">Implementace <xref:System.Windows.Input.ICommand> rozhraní se často používá s vzoru MVVM.</span><span class="sxs-lookup"><span data-stu-id="117eb-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="117eb-138">Následující příklad ukazuje implementaci <xref:System.Windows.Input.ICommand> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="117eb-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="117eb-139">Následující příklad ukazuje zjednodušený model.</span><span class="sxs-lookup"><span data-stu-id="117eb-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="117eb-140">Zobrazit</span><span class="sxs-lookup"><span data-stu-id="117eb-140">View</span></span>  
 <span data-ttu-id="117eb-141">Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikace, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci, založené na technologii Silverlight aplikaci nebo aplikaci Windows Phone 7.5, můžete odkazovat sestavení, které obsahuje projekty model modelu a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="117eb-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="117eb-142">Můžete vytvořit zobrazení, která komunikuje pomocí zobrazení modelu.</span><span class="sxs-lookup"><span data-stu-id="117eb-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="117eb-143">Následující příklad ukazuje zjednodušený aplikace Windows Presentation Foundation (WPF), načte a aktualizaci dat z modelu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="117eb-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="117eb-144">Můžete vytvořit v programu Silverlight, Windows Phone, podobně jako zobrazení nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="117eb-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="117eb-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="117eb-145">See also</span></span>

- [<span data-ttu-id="117eb-146">Přenosná knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="117eb-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
