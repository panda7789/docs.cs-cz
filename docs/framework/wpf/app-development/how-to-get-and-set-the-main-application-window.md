---
title: 'Postupy: získání a nastavení hlavního okna aplikace'
description: Podle tohoto příkladu můžete získat a nastavit hlavní okno aplikace v rámci aplikace Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 9bb5bce9b90482796acd8c62e77dc8bd9a850eeb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622676"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Postupy: získání a nastavení hlavního okna aplikace
Tento příklad ukazuje, jak získat a nastavit hlavní okno aplikace.  
  
## <a name="example"></a>Příklad  
 První <xref:System.Windows.Window> instance, která je vytvořena v rámci aplikace Windows Presentation Foundation (WPF), je automaticky nastavena <xref:System.Windows.Application> jako hlavní okno aplikace. Prvním <xref:System.Windows.Window> vytvořeným instancem bude pravděpodobně okno, které je zadáno jako spouštěcí identifikátor URI (viz <xref:System.Windows.Application.StartupUri%2A> ).  
  
 Prvním <xref:System.Windows.Window> může být také vytvoření instance pomocí kódu. Jedním z příkladů je otevření okna během spouštění aplikace, jako například následující:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 V některých případech první vytvořená instance není <xref:System.Windows.Window> ve skutečnosti hlavní okno aplikace, například úvodní obrazovka. V takovém případě můžete určit hlavní okno aplikace pomocí značek, například takto:  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Bez ohledu na to, jestli je hlavní okno zadané automaticky nebo ručně, můžete získat hlavní okno <xref:System.Windows.Application.MainWindow%2A> s použitím následujícího kódu, jako je třeba toto:  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
