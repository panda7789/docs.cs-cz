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
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="a970a-102">Postupy: získání a nastavení hlavního okna aplikace</span><span class="sxs-lookup"><span data-stu-id="a970a-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="a970a-103">Tento příklad ukazuje, jak získat a nastavit hlavní okno aplikace.</span><span class="sxs-lookup"><span data-stu-id="a970a-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a970a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a970a-104">Example</span></span>  
 <span data-ttu-id="a970a-105">První <xref:System.Windows.Window>, který je vytvořen v rámci aplikace Windows Presentation Foundation (WPF), je automaticky nastavena <xref:System.Windows.Application> jako hlavní okno aplikace.</span><span class="sxs-lookup"><span data-stu-id="a970a-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="a970a-106">První <xref:System.Windows.Window>, který má být vytvořen jako instance, bude pravděpodobně okno, které je zadáno jako spouštěcí identifikátor URI (Uniform Resource Identifier) (viz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="a970a-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup uniform resource identifier (URI) (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="a970a-107">První <xref:System.Windows.Window> může být také vytvořena pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="a970a-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="a970a-108">Jedním z příkladů je otevření okna během spouštění aplikace, jako například následující:</span><span class="sxs-lookup"><span data-stu-id="a970a-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="a970a-109">Někdy první vytvořená instance <xref:System.Windows.Window> není ve skutečnosti hlavní okno aplikace, například úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="a970a-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="a970a-110">V takovém případě můžete určit hlavní okno aplikace pomocí značek, například takto:</span><span class="sxs-lookup"><span data-stu-id="a970a-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="a970a-111">Bez ohledu na to, jestli je hlavní okno zadané automaticky nebo ručně, můžete získat hlavní okno z <xref:System.Windows.Application.MainWindow%2A> pomocí následujícího kódu, například takto:</span><span class="sxs-lookup"><span data-stu-id="a970a-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
