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
ms.openlocfilehash: 445cf4178b90719f923b66a7778f60c1bc846766
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204977"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)
Můžete použít .NET Framework [přenosné knihovny tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) k implementaci vzoru Model-View-View Model (MVVM) a sdílet sestavení napříč různými platformami.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM je model aplikace, který izoluje uživatelské rozhraní od základní obchodní logiky. Můžete implementovat model a zobrazení tříd modelu v projektu přenositelné knihovny tříd v aplikaci Visual Studio 2012 a pak vytvořit zobrazení, která jsou přizpůsobená pro různé platformy. Tento přístup umožňuje napsat datový model a obchodní logiku pouze jednou a použít tento kód z aplikací pro Store .NET Framework, Silverlight, Windows Phone a Windows 8. x, jak je znázorněno na následujícím obrázku.

 ![Zobrazuje přenosnou knihovnu tříd s MVVM sdílenými sestaveními napříč platformami.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Toto téma neposkytuje obecné informace o vzoru MVVM. Poskytuje pouze informace o tom, jak použít přenosnou knihovnu tříd k implementaci MVVM. Další informace o MVVM najdete v tématu [rychlý Start MVVM s Prism Library 5,0 pro WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Třídy, které podporují MVVM
 Při cílení na .NET Framework 4,5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight nebo Windows Phone 7,5 pro váš přenosný projekt knihovny tříd jsou k dispozici následující třídy pro implementaci MVVM vzoru:

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> – třída

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> – třída

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> – třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> – třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> – třída

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> – třída

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> – třída

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> – třída

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> – třída

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> – třída

- Všechny třídy v oboru názvů <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>Implementace MVVM
 Pro implementaci MVVM obvykle vytvoříte model i model zobrazení v přenositelném projektu knihovny tříd, protože Přenosná knihovna tříd nemůže odkazovat na nepřenosný projekt. Model a model zobrazení mohou být ve stejném projektu nebo v samostatných projektech. Použijete-li samostatné projekty, přidejte odkaz z projektu modelu zobrazení do projektu modelu.

 Po zkompilování projektů modelu a zobrazení modelu odkazujete na tato sestavení v aplikaci, která obsahuje zobrazení. Pokud zobrazení komunikuje pouze s modelem zobrazení, stačí odkazovat pouze na sestavení, které obsahuje model zobrazení.

### <a name="model"></a>Model
 Následující příklad ukazuje zjednodušenou třídu modelu, která může být uložena v přenositelném projektu knihovny tříd.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 Následující příklad ukazuje jednoduchý způsob, jak naplnit, načítat a aktualizovat data v přenositelném projektu knihovny tříd. Ve skutečné aplikaci byste načetli data ze zdroje, jako je služba Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Zobrazit model
 Základní třída pro modely zobrazení je často přidána při implementaci vzoru MVVM. Následující příklad ukazuje základní třídu.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Implementace rozhraní <xref:System.Windows.Input.ICommand> se často používá se vzorem MVVM. Následující příklad ukazuje implementaci rozhraní <xref:System.Windows.Input.ICommand>.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 Následující příklad ukazuje zjednodušený model zobrazení.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Zobrazit  
 Z aplikace .NET Framework 4,5, aplikace pro Store v systému Windows 8. x, aplikace založené na technologii Silverlight nebo aplikace Windows Phone 7,5 můžete odkazovat na sestavení, které obsahuje model a zobrazení projektů modelu.  Pak vytvoříte zobrazení, které komunikuje s modelem zobrazení. Následující příklad ukazuje zjednodušenou aplikaci Windows Presentation Foundation (WPF), která načítá a aktualizuje data z modelu zobrazení. Podobná zobrazení můžete vytvořit v aplikacích Silverlight, Windows Phone nebo Windows 8. x Store.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Viz také:

- [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
