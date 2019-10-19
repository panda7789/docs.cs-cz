---
title: 'Postupy: získání a nastavení hlavního okna aplikace'
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
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582549"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Postupy: získání a nastavení hlavního okna aplikace
Tento příklad ukazuje, jak získat a nastavit hlavní okno aplikace.  
  
## <a name="example"></a>Příklad  
 První <xref:System.Windows.Window>, který je vytvořen v rámci aplikace Windows Presentation Foundation (WPF), je automaticky nastavena <xref:System.Windows.Application> jako hlavní okno aplikace. První <xref:System.Windows.Window>, který má být vytvořen jako instance, bude pravděpodobně okno, které je zadáno jako spouštěcí identifikátor URI (Uniform Resource Identifier) (viz <xref:System.Windows.Application.StartupUri%2A>).  
  
 První <xref:System.Windows.Window> může být také vytvořena pomocí kódu. Jedním z příkladů je otevření okna během spouštění aplikace, jako například následující:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Někdy první vytvořená instance <xref:System.Windows.Window> není ve skutečnosti hlavní okno aplikace, například úvodní obrazovka. V takovém případě můžete určit hlavní okno aplikace pomocí značek, například takto:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Bez ohledu na to, jestli je hlavní okno zadané automaticky nebo ručně, můžete získat hlavní okno z <xref:System.Windows.Application.MainWindow%2A> pomocí následujícího kódu, například takto:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
