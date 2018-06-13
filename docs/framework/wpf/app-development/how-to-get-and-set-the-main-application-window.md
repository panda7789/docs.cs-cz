---
title: 'Postupy: získání a nastavení hlavní okno aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: ae70b482eba8fb4e0bf587def06bb90d751a4312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547979"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Postupy: získání a nastavení hlavní okno aplikace
Tento příklad ukazuje, jak k získání a nastavení hlavního okna aplikace.  
  
## <a name="example"></a>Příklad  
 První <xref:System.Windows.Window> vytvoření instance v rámci Windows Presentation Foundation (WPF) aplikace je automaticky nastaven na <xref:System.Windows.Application> jako hlavní okno aplikace. První <xref:System.Windows.Window> být instancí bude pravděpodobně možné okně, které je zadán jako počáteční [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (viz <xref:System.Windows.Application.StartupUri%2A>).  
  
 První <xref:System.Windows.Window> může také být vytvořena instance pomocí kódu. Jedním z příkladů je otevřete okno při spuštění aplikace, jako jsou následující:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 V některých případech první instanci <xref:System.Windows.Window> je ve skutečnosti není okno hlavní aplikace například úvodní obrazovka. V takovém případě můžete určit hlavní okno aplikace pomocí značek, podobně jako tento:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Zda hlavní okno je zadána automaticky nebo ručně, můžete získat z hlavního okna <xref:System.Windows.Application.MainWindow%2A> pomocí následujícího kódu, třeba takto:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
