---
title: "Postupy: Přidání úvodní obrazovky do aplikace WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed9669479a3854c843716a1aeb37f7701ea7d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="a1e11-102">Postupy: Přidání úvodní obrazovky do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="a1e11-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="a1e11-103">Toto téma ukazuje, jak přidat okno spuštění nebo *úvodní obrazovka*, k aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a1e11-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="a1e11-104">Chcete-li přidat bitovou kopii existující jako úvodní obrazovka</span><span class="sxs-lookup"><span data-stu-id="a1e11-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="a1e11-105">Vytvořit nebo najít bitovou kopii, kterou chcete použít pro úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="a1e11-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="a1e11-106">Můžete použít všechny bitové kopie formátu, který je podporován ve vytváření bitové kopie součást WIC (Windows).</span><span class="sxs-lookup"><span data-stu-id="a1e11-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="a1e11-107">Například můžete pomocí formátu BMP, GIF, JPEG, PNG nebo TIFF.</span><span class="sxs-lookup"><span data-stu-id="a1e11-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="a1e11-108">Přidání souboru bitové kopie do projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="a1e11-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="a1e11-109">Další informace najdete v tématu [NIB: postupy: Přidání existujících položek do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="a1e11-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="a1e11-110">V Průzkumníku řešení vyberte bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="a1e11-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="a1e11-111">V okně vlastností klikněte na šipku rozevíracího seznamu pro **akce sestavení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1e11-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="a1e11-112">Vyberte **SplashScreen** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="a1e11-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1e11-113">Pokud se nezobrazí **SplashScreen** možnost, zkontrolujte, že používáte [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a1e11-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="a1e11-114">Stisknutím klávesy F5 sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e11-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="a1e11-115">Obrázek úvodní obrazovky se zobrazí v centru obrazovky a pak zmenšuje až se zobrazí okno hlavní aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1e11-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="a1e11-116">Chcete-li odebrat úvodní obrazovka z aplikace</span><span class="sxs-lookup"><span data-stu-id="a1e11-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="a1e11-117">V Průzkumníku řešení vyberte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="a1e11-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="a1e11-118">V okně vlastnosti nastavit **akce sestavení** k **žádné**.</span><span class="sxs-lookup"><span data-stu-id="a1e11-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="a1e11-119">Chcete-li odebrat úvodní obrazovka z aplikace</span><span class="sxs-lookup"><span data-stu-id="a1e11-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="a1e11-120">V Průzkumníku řešení odstraňte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="a1e11-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="a1e11-121">Obrázek úvodní obrazovky vylučte z projektu.</span><span class="sxs-lookup"><span data-stu-id="a1e11-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e11-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1e11-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="a1e11-123">NIB: postupy: Přidání existujících položek do projektu</span><span class="sxs-lookup"><span data-stu-id="a1e11-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
