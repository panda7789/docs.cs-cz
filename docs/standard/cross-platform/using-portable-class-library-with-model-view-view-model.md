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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: da1a05a6003d93727efd5749aac9a055c8c80d38
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Používání knihovny přenosných tříd spolu s modelem MVVM (Model-View-View Model)
Můžete použít rozhraní .NET Framework [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) implementovat vzor Model-View-View Model (modelem MVVM) a sdílení sestavení napříč různými platformami.  
  
 Rozhraní MVVM je application vzor, který izoluje uživatelské rozhraní z základní obchodní logiky. Můžete implementovat třídy modelu modelu a zobrazení v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]a poté vytvořit zobrazení, které jsou přizpůsobené pro různé platformy. Tento přístup umožňuje zapsat data modelu a obchodní logiku jenom jednou a které code z rozhraní .NET Framework, Silverlight, Windows Phone a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací, jak je znázorněno na následujícím obrázku.  
  
 ![Přenosné s modelem MVVM diagram](../../../docs/standard/cross-platform/media/portablemvvmdiagram.png "PortableMVVMdiagram")  
  
 Toto téma neposkytuje obecné informace o rozhraní MVVM vzor. Pouze poskytuje informace o tom, jak používat [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] implementovat rozhraní MVVM. Další informace o rozhraní MVVM najdete v tématu [rychlý start modelem MVVM](http://go.microsoft.com/fwlink/?LinkId=234934).  
  
## <a name="classes-that-support-mvvm"></a>Třídy, které podporují rozhraní MVVM  
 Pokud cílíte [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, nebo Windows Phone 7.5 pro vaše [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu následující třídy jsou k dispozici pro implementaci rozhraní MVVM vzoru:  
  
-   <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>– Třída  
  
-   <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>– Třída  
  
-   <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>– Třída  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>– Třída  
  
-   <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>– Třída  
  
-   Všechny třídy v <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> obor názvů  
  
## <a name="implementing-mvvm"></a>Implementace rozhraní MVVM  
 K implementaci rozhraní MVVM, obvykle vytvoříte model a model v zobrazení [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu, protože [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu nemůže odkazovat na jiné přenositelností projektu. Model a model zobrazení může být ve stejném projektu nebo v samostatné projekty. Pokud použijete samostatné projekty, přidejte do projektu modelu odkaz z projektu modelu zobrazení.  
  
 Po kompilace modelu a zobrazit projekty modelu, můžete odkazovat na tyto sestavení v aplikaci, která obsahuje zobrazení. Pokud zobrazení pracuje pouze s modelu zobrazení, stačí odkazovat na sestavení, které obsahuje zobrazení modelu.  
  
### <a name="model"></a>Model  
 Následující příklad ukazuje zjednodušený model třídu, která může být umístěn v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu.  
  
 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]  
  
 Následující příklad ukazuje jednoduchý způsob, jak naplnit načíst a aktualizovat data v [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projektu. V reálné aplikaci byste načíst data ze zdroje, například služby Windows Communication Foundation (WCF).  
  
 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]  
  
### <a name="view-model"></a>Model zobrazení  
 Základní třída pro zobrazení modely je často přidat při implementaci rozhraní MVVM vzor. Následující příklad ukazuje základní třídu.  
  
 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]  
  
 Implementace <xref:System.Windows.Input.ICommand> rozhraní se často používá s modelem MVVM vzor. Následující příklad ukazuje implementaci <xref:System.Windows.Input.ICommand> rozhraní.  
  
 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]  
  
 Následující příklad ukazuje Zjednodušený pohled modelu.  
  
 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Zobrazit  
 Z [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aplikaci [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace, založená na technologii Silverlight aplikace nebo aplikace Windows Phone 7.5, můžete odkazovat sestavení, které obsahuje projekty model modelu a zobrazení.  Můžete vytvořit zobrazení, která komunikuje pomocí zobrazení modelu. Následující příklad ukazuje zjednodušený aplikaci Windows Presentation Foundation (WPF), která načte a aktualizuje data v zobrazení modelu. Můžete vytvořit v programu Silverlight, Windows Phone, podobně jako zobrazení nebo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Viz také  
 [Přenosná knihovna tříd](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
