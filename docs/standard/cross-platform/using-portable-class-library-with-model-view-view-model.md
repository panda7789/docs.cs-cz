---
title: "Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e39a8df5c8aee05414e778f15a29bbeda8dba930
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="302cb-102">Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)</span><span class="sxs-lookup"><span data-stu-id="302cb-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="302cb-103">Můžete použít rozhraní .NET Framework [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementovat vzor Model-View-View Model (modelem MVVM) a sdílení sestavení napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="302cb-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>  
  
 <span data-ttu-id="302cb-104">Rozhraní MVVM je application vzor, který izoluje uživatelské rozhraní z základní obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="302cb-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="302cb-105">Můžete implementovat třídy modelu modelu a zobrazení v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]a poté vytvořit zobrazení, které jsou přizpůsobené pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="302cb-105">You can implement the model and view model classes in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], and then create views that are customized for different platforms.</span></span> <span data-ttu-id="302cb-106">Tento přístup umožňuje zapsat data modelu a obchodní logiku jenom jednou a které code z rozhraní .NET Framework, Silverlight, Windows Phone a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="302cb-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="302cb-107">![Přenosné s modelem MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span><span class="sxs-lookup"><span data-stu-id="302cb-107">![Portable with MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")</span></span>  
  
 <span data-ttu-id="302cb-108">Toto téma neposkytuje obecné informace o rozhraní MVVM vzor.</span><span class="sxs-lookup"><span data-stu-id="302cb-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="302cb-109">Pouze poskytuje informace o tom, jak používat [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] implementovat rozhraní MVVM.</span><span class="sxs-lookup"><span data-stu-id="302cb-109">It only provides information about how to use [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] to implement MVVM.</span></span> <span data-ttu-id="302cb-110">Další informace o rozhraní MVVM najdete v tématu [rychlý start modelem MVVM](http://go.microsoft.com/fwlink/?LinkId=234934).</span><span class="sxs-lookup"><span data-stu-id="302cb-110">For more information about MVVM, see the [MVVM Quickstart](http://go.microsoft.com/fwlink/?LinkId=234934).</span></span>  
  
## <a name="classes-that-support-mvvm"></a><span data-ttu-id="302cb-111">Třídy, které podporují rozhraní MVVM</span><span class="sxs-lookup"><span data-stu-id="302cb-111">Classes That Support MVVM</span></span>  
 <span data-ttu-id="302cb-112">Pokud cílíte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, nebo Windows Phone 7.5 pro vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu následující třídy jsou k dispozici pro implementaci rozhraní MVVM vzoru:</span><span class="sxs-lookup"><span data-stu-id="302cb-112">When you target the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, the following classes are available for implementing the MVVM pattern:</span></span>  
  
-   <span data-ttu-id="302cb-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType>– Třída</span><span class="sxs-lookup"><span data-stu-id="302cb-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>  
  
-   <span data-ttu-id="302cb-123">Všechny třídy v <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> obor názvů</span><span class="sxs-lookup"><span data-stu-id="302cb-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>  
  
## <a name="implementing-mvvm"></a><span data-ttu-id="302cb-124">Implementace rozhraní MVVM</span><span class="sxs-lookup"><span data-stu-id="302cb-124">Implementing MVVM</span></span>  
 <span data-ttu-id="302cb-125">K implementaci rozhraní MVVM, obvykle vytvoříte model a model v zobrazení [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, protože [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nemůže odkazovat na jiné přenositelností projektu.</span><span class="sxs-lookup"><span data-stu-id="302cb-125">To implement MVVM, you typically create both the model and the view model in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, because a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project cannot reference a non-portable project.</span></span> <span data-ttu-id="302cb-126">Model a model zobrazení může být ve stejném projektu nebo v samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="302cb-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="302cb-127">Pokud použijete samostatné projekty, přidejte do projektu modelu odkaz z projektu modelu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="302cb-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>  
  
 <span data-ttu-id="302cb-128">Po kompilace modelu a zobrazit projekty modelu, můžete odkazovat na tyto sestavení v aplikaci, která obsahuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="302cb-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="302cb-129">Pokud zobrazení pracuje pouze s modelu zobrazení, stačí odkazovat na sestavení, které obsahuje zobrazení modelu.</span><span class="sxs-lookup"><span data-stu-id="302cb-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>  
  
### <a name="model"></a><span data-ttu-id="302cb-130">Model</span><span class="sxs-lookup"><span data-stu-id="302cb-130">Model</span></span>  
 <span data-ttu-id="302cb-131">Následující příklad ukazuje zjednodušený model třídu, která může být umístěn v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="302cb-131">The following example shows a simplified model class that could reside in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 <span data-ttu-id="302cb-132">Následující příklad ukazuje jednoduchý způsob, jak naplnit načíst a aktualizovat data v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="302cb-132">The following example shows a simple way to populate, retrieve, and update the data in a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project.</span></span> <span data-ttu-id="302cb-133">V reálné aplikaci byste načíst data ze zdroje, například služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="302cb-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a><span data-ttu-id="302cb-134">Model zobrazení</span><span class="sxs-lookup"><span data-stu-id="302cb-134">View Model</span></span>  
 <span data-ttu-id="302cb-135">Základní třída pro zobrazení modely je často přidat při implementaci rozhraní MVVM vzor.</span><span class="sxs-lookup"><span data-stu-id="302cb-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="302cb-136">Následující příklad ukazuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="302cb-136">The following example shows a base class.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 <span data-ttu-id="302cb-137">Implementace <xref:System.Windows.Input.ICommand> rozhraní se často používá s modelem MVVM vzor.</span><span class="sxs-lookup"><span data-stu-id="302cb-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="302cb-138">Následující příklad ukazuje implementaci <xref:System.Windows.Input.ICommand> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="302cb-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 <span data-ttu-id="302cb-139">Následující příklad ukazuje Zjednodušený pohled modelu.</span><span class="sxs-lookup"><span data-stu-id="302cb-139">The following example shows a simplified view model.</span></span>  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="302cb-140">Zobrazit</span><span class="sxs-lookup"><span data-stu-id="302cb-140">View</span></span>  
 <span data-ttu-id="302cb-141">Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikaci [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, založená na technologii Silverlight aplikace nebo aplikace Windows Phone 7.5, můžete odkazovat sestavení, které obsahuje projekty model modelu a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="302cb-141">From a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="302cb-142">Můžete vytvořit zobrazení, která komunikuje pomocí zobrazení modelu.</span><span class="sxs-lookup"><span data-stu-id="302cb-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="302cb-143">Následující příklad ukazuje zjednodušený aplikaci Windows Presentation Foundation (WPF), která načte a aktualizuje data v zobrazení modelu.</span><span class="sxs-lookup"><span data-stu-id="302cb-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="302cb-144">Můžete vytvořit v programu Silverlight, Windows Phone, podobně jako zobrazení nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="302cb-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="302cb-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="302cb-145">See Also</span></span>  
 [<span data-ttu-id="302cb-146">Přenosná knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="302cb-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
