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
ms.openlocfilehash: 3aa18d4498bcdcc3737311473b4736545b184395
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003776"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)
Můžete použít rozhraní .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementovat vzor Model-View-View Model (MVVM) a sdílet sestavení napříč různými platformami.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM je vzorek aplikace, který izoluje uživatelského rozhraní ze základní obchodní logiku. Můžete implementovat modelu a zobrazení tříd modelu v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu v sadě Visual Studio 2012 a pak vytvořte zobrazení, která jsou přizpůsobená pro různé platformy. Tento přístup umožňuje zapisovat data model a obchodní logiky pouze jednou a použít tento kód v rozhraní .NET Framework, Silverlight, Windows Phone a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, jak je znázorněno na následujícím obrázku.

 ![Ukazuje přenosné knihovny tříd s modelem MVVM sdílení sestavení napříč platformami.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Toto téma neposkytuje obecné informace o vzoru MVVM. Nabízí informace o tom, jak používat [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] implementovat MVVM. Další informace o MVVM, najdete v článku [MVVM rychlém startu pomocí knihovny 5.0 modulu Prism pro WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Třídy, které podporují MVVM
 Pokud cílíte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight nebo Windows Phone 7.5 pro vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, jsou k dispozici pro implementaci vzoru MVVM následující třídy:

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> Třída

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> Třída

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> Třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> Třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> Třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> Třída

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> Třída

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> Třída

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> Třída

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> Třída

- Všechny třídy v <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> obor názvů

## <a name="implementing-mvvm"></a>Implementace MVVM
 K implementaci MVVM, obvykle vytvoříte model a model v zobrazení [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, protože [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] nepřenositelný projekt nemůže odkazovat na projekt. Model a model zobrazení může být ve stejném projektu nebo v samostatné projekty. Pokud používáte samostatné projekty, přidejte odkaz z projektu zobrazení modelu do projektu s modelem.

 Po kompilaci modelu a zobrazit projekty modelu, můžete odkazovat na tato sestavení v aplikaci, která obsahuje zobrazení. Pokud zobrazení pracuje pouze s model zobrazení, stačí odkazovat na sestavení, který obsahuje model zobrazení.

### <a name="model"></a>Model
 Následující příklad ukazuje zjednodušený model třídu, která může být umístěn v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 Následující příklad ukazuje jednoduchý způsob, jak naplnit, načíst a aktualizovat data v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu. V reálné aplikaci byste načíst data ze zdroje, jako je například služba Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Model zobrazení
 Základní třída pro zobrazení modely se často přidá při implementaci vzoru MVVM. Následující příklad ukazuje základní třídu.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Implementace <xref:System.Windows.Input.ICommand> rozhraní se často používá s vzoru MVVM. Následující příklad ukazuje implementaci <xref:System.Windows.Input.ICommand> rozhraní.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 Následující příklad ukazuje zjednodušený model.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Zobrazit  
 Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikace, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikaci, založené na technologii Silverlight aplikaci nebo aplikaci Windows Phone 7.5, můžete odkazovat sestavení, které obsahuje projekty model modelu a zobrazení.  Můžete vytvořit zobrazení, která komunikuje pomocí zobrazení modelu. Následující příklad ukazuje zjednodušený aplikace Windows Presentation Foundation (WPF), načte a aktualizaci dat z modelu zobrazení. Můžete vytvořit v programu Silverlight, Windows Phone, podobně jako zobrazení nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Viz také:

- [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
