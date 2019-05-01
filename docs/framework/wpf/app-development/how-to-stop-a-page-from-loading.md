---
title: 'Postupy: Zastavení načítání stránky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], stopping from loading
- methods [WPF], Stoploading
- events [WPF], NavigationStopped
- NavigationStopped properties [WPF]
- stopping pages from loading [WPF]
- loading [WPF], stopping
ms.assetid: e2b695b0-517e-462c-8ccf-90cc8d6ba864
ms.openlocfilehash: c5694bb2cb6c618cd84bad3dc893ae3855e44892
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006678"
---
# <a name="how-to-stop-a-page-from-loading"></a>Postupy: Zastavení načítání stránky
Tento příklad ukazuje, jak volat <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> metoda zastavit přechod na obsah, než se dokončí stahování.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Navigation.NavigationWindow.StopLoading%2A> Zastaví stahování požadovaného obsahu a způsobí, že <xref:System.Windows.Navigation.NavigationWindow.NavigationStopped> vyvolána událost.  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatestoploadingcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateStopLoadingCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatestoploadingcode)]
