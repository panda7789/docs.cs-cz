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
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="a8dc0-103">Postupy: získání a nastavení hlavního okna aplikace</span><span class="sxs-lookup"><span data-stu-id="a8dc0-103">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="a8dc0-104">Tento příklad ukazuje, jak získat a nastavit hlavní okno aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8dc0-104">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8dc0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8dc0-105">Example</span></span>  
 <span data-ttu-id="a8dc0-106">První <xref:System.Windows.Window> instance, která je vytvořena v rámci aplikace Windows Presentation Foundation (WPF), je automaticky nastavena <xref:System.Windows.Application> jako hlavní okno aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8dc0-106">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="a8dc0-107">Prvním <xref:System.Windows.Window> vytvořeným instancem bude pravděpodobně okno, které je zadáno jako spouštěcí identifikátor URI (viz <xref:System.Windows.Application.StartupUri%2A> ).</span><span class="sxs-lookup"><span data-stu-id="a8dc0-107">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup uniform resource identifier (URI) (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="a8dc0-108">Prvním <xref:System.Windows.Window> může být také vytvoření instance pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="a8dc0-108">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="a8dc0-109">Jedním z příkladů je otevření okna během spouštění aplikace, jako například následující:</span><span class="sxs-lookup"><span data-stu-id="a8dc0-109">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="a8dc0-110">V některých případech první vytvořená instance není <xref:System.Windows.Window> ve skutečnosti hlavní okno aplikace, například úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="a8dc0-110">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="a8dc0-111">V takovém případě můžete určit hlavní okno aplikace pomocí značek, například takto:</span><span class="sxs-lookup"><span data-stu-id="a8dc0-111">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="a8dc0-112">Bez ohledu na to, jestli je hlavní okno zadané automaticky nebo ručně, můžete získat hlavní okno <xref:System.Windows.Application.MainWindow%2A> s použitím následujícího kódu, jako je třeba toto:</span><span class="sxs-lookup"><span data-stu-id="a8dc0-112">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
