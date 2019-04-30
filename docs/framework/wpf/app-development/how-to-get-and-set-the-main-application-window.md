---
title: 'Postupy: Získání a nastavení hlavního okna aplikace'
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
ms.openlocfilehash: ea8333aa82f1159afb438215940ee1e7c2605e96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947794"
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="28d66-102">Postupy: Získání a nastavení hlavního okna aplikace</span><span class="sxs-lookup"><span data-stu-id="28d66-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="28d66-103">Tento příklad ukazuje, jak k získání a nastavení hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="28d66-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28d66-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="28d66-104">Example</span></span>  
 <span data-ttu-id="28d66-105">První <xref:System.Windows.Window> , která je vytvořena instance v rámci Windows Presentation Foundation (WPF) aplikace je automaticky nastaven na <xref:System.Windows.Application> jako hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="28d66-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="28d66-106">První <xref:System.Windows.Window> bude instance bude pravděpodobně možné okna, který je zadán jako počáteční [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (viz <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="28d66-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="28d66-107">První <xref:System.Windows.Window> může také vytvořit instanci pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="28d66-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="28d66-108">Jedním z příkladů je otevřete okno při spuštění aplikace, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="28d66-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="28d66-109">V některých případech první instance <xref:System.Windows.Window> je ve skutečnosti hlavního okna aplikace například úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="28d66-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="28d66-110">V takovém případě můžete zadat hlavního okna aplikace pomocí značek, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="28d66-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="28d66-111">Specifikovaných hlavní okno se automaticky nebo ručně, můžete získat z hlavního okna <xref:System.Windows.Application.MainWindow%2A> pomocí následujícího kódu, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="28d66-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
