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
ms.openlocfilehash: 87e756445255f1bd2417a06dfa611eba23208575
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716744"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="4c65c-102">Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)</span><span class="sxs-lookup"><span data-stu-id="4c65c-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="4c65c-103">Můžete použít .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) k implementaci vzoru Model-View-View Model (MVVM) a sdílet sestavení napříč různými platformami.</span><span class="sxs-lookup"><span data-stu-id="4c65c-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="4c65c-104">MVVM je model aplikace, který izoluje uživatelské rozhraní od základní obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="4c65c-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="4c65c-105">Můžete implementovat model a zobrazení tříd modelu v projektu přenositelné knihovny tříd v aplikaci Visual Studio 2012 a pak vytvořit zobrazení, která jsou přizpůsobená pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="4c65c-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="4c65c-106">Tento přístup umožňuje napsat datový model a obchodní logiku pouze jednou a použít tento kód z aplikací pro Store .NET Framework, Silverlight, Windows Phone a Windows 8. x, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="4c65c-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Zobrazuje přenosnou knihovnu tříd s MVVM sdílenými sestaveními napříč platformami.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="4c65c-108">Toto téma neposkytuje obecné informace o vzoru MVVM.</span><span class="sxs-lookup"><span data-stu-id="4c65c-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="4c65c-109">Poskytuje pouze informace o tom, jak použít přenosnou knihovnu tříd k implementaci MVVM.</span><span class="sxs-lookup"><span data-stu-id="4c65c-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="4c65c-110">Další informace o MVVM najdete v tématu [rychlý Start MVVM s Prism Library 5,0 pro WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="4c65c-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="4c65c-111">Třídy, které podporují MVVM</span><span class="sxs-lookup"><span data-stu-id="4c65c-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="4c65c-112">Při cílení na .NET Framework 4,5, .NET pro Windows 8. x Store aplikace, Silverlight nebo Windows Phone 7,5 pro váš přenosný projekt knihovny tříd jsou k dispozici následující třídy pro implementaci MVVM vzoru:</span><span class="sxs-lookup"><span data-stu-id="4c65c-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="4c65c-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> – třída</span><span class="sxs-lookup"><span data-stu-id="4c65c-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="4c65c-123">Všechny třídy v oboru názvů <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4c65c-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="4c65c-124">Implementace MVVM</span><span class="sxs-lookup"><span data-stu-id="4c65c-124">Implementing MVVM</span></span>
 <span data-ttu-id="4c65c-125">Pro implementaci MVVM obvykle vytvoříte model i model zobrazení v přenositelném projektu knihovny tříd, protože Přenosná knihovna tříd nemůže odkazovat na nepřenosný projekt.</span><span class="sxs-lookup"><span data-stu-id="4c65c-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="4c65c-126">Model a model zobrazení mohou být ve stejném projektu nebo v samostatných projektech.</span><span class="sxs-lookup"><span data-stu-id="4c65c-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="4c65c-127">Použijete-li samostatné projekty, přidejte odkaz z projektu modelu zobrazení do projektu modelu.</span><span class="sxs-lookup"><span data-stu-id="4c65c-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="4c65c-128">Po zkompilování projektů modelu a zobrazení modelu odkazujete na tato sestavení v aplikaci, která obsahuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4c65c-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="4c65c-129">Pokud zobrazení komunikuje pouze s modelem zobrazení, stačí odkazovat pouze na sestavení, které obsahuje model zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4c65c-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="4c65c-130">Model</span><span class="sxs-lookup"><span data-stu-id="4c65c-130">Model</span></span>
 <span data-ttu-id="4c65c-131">Následující příklad ukazuje zjednodušenou třídu modelu, která může být uložena v přenositelném projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="4c65c-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="4c65c-132">Následující příklad ukazuje jednoduchý způsob, jak naplnit, načítat a aktualizovat data v přenositelném projektu knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="4c65c-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="4c65c-133">Ve skutečné aplikaci byste načetli data ze zdroje, jako je služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4c65c-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="4c65c-134">Zobrazit model</span><span class="sxs-lookup"><span data-stu-id="4c65c-134">View Model</span></span>
 <span data-ttu-id="4c65c-135">Základní třída pro modely zobrazení je často přidána při implementaci vzoru MVVM.</span><span class="sxs-lookup"><span data-stu-id="4c65c-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="4c65c-136">Následující příklad ukazuje základní třídu.</span><span class="sxs-lookup"><span data-stu-id="4c65c-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="4c65c-137">Implementace rozhraní <xref:System.Windows.Input.ICommand> se často používá se vzorem MVVM.</span><span class="sxs-lookup"><span data-stu-id="4c65c-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="4c65c-138">Následující příklad ukazuje implementaci rozhraní <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="4c65c-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="4c65c-139">Následující příklad ukazuje zjednodušený model zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4c65c-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="4c65c-140">Podívejte se na téma .</span><span class="sxs-lookup"><span data-stu-id="4c65c-140">View</span></span>  
 <span data-ttu-id="4c65c-141">Z aplikace .NET Framework 4,5, aplikace pro Store v systému Windows 8. x, aplikace založené na technologii Silverlight nebo aplikace Windows Phone 7,5 můžete odkazovat na sestavení, které obsahuje model a zobrazení projektů modelu.</span><span class="sxs-lookup"><span data-stu-id="4c65c-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="4c65c-142">Pak vytvoříte zobrazení, které komunikuje s modelem zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4c65c-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="4c65c-143">Následující příklad ukazuje zjednodušenou aplikaci Windows Presentation Foundation (WPF), která načítá a aktualizuje data z modelu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="4c65c-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="4c65c-144">Podobná zobrazení můžete vytvořit v aplikacích Silverlight, Windows Phone nebo Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="4c65c-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4c65c-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c65c-145">See also</span></span>

- [<span data-ttu-id="4c65c-146">Přenosná knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="4c65c-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
