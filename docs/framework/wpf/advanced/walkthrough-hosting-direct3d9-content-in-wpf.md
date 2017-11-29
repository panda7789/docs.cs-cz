---
title: "Návod: Hostování obsahu Direct3D9 ve WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec80eed37777fc7b17b435e1bef63ecbb94bdf46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="bf515-102">Návod: Hostování obsahu Direct3D9 ve WPF</span><span class="sxs-lookup"><span data-stu-id="bf515-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="bf515-103">Tento návod ukazuje, jak pro hostování procesu Direct3D9 obsahu v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="bf515-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="bf515-104">V tomto návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bf515-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="bf515-105">Vytvořte projekt WPF pro hostování daného obsahu procesu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="bf515-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="bf515-106">Importujte procesu Direct3D9 obsah.</span><span class="sxs-lookup"><span data-stu-id="bf515-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="bf515-107">Zobrazit obsah procesu Direct3D9 pomocí <xref:System.Windows.Interop.D3DImage> třídy.</span><span class="sxs-lookup"><span data-stu-id="bf515-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="bf515-108">Jakmile budete hotovi, budete vědět, jak pro hostování procesu Direct3D9 obsahu v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="bf515-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bf515-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf515-109">Prerequisites</span></span>  
 <span data-ttu-id="bf515-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="bf515-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="bf515-111">.</span><span class="sxs-lookup"><span data-stu-id="bf515-111">.</span></span>  
  
-   <span data-ttu-id="bf515-112">DirectX SDK 9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="bf515-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="bf515-113">Knihovny DLL, která obsahuje procesu Direct3D9 obsah ve formátu WPF kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="bf515-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="bf515-114">Další informace najdete v tématu [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) a [návod: vytváření obsahu procesu Direct3D9 pro hostitelský v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="bf515-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="bf515-115">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="bf515-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="bf515-116">Prvním krokem je vytvoření projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="bf515-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="bf515-117">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="bf515-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="bf515-118">Vytvořte nový projekt aplikace WPF v jazyce Visual C# s názvem `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="bf515-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="bf515-119">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="bf515-119">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="bf515-120">Otevře se v MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf515-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="bf515-121">Import procesu Direct3D9 obsah</span><span class="sxs-lookup"><span data-stu-id="bf515-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="bf515-122">Importovat obsah procesu Direct3D9 z nespravovaných knihovny DLL pomocí `DllImport` atribut.</span><span class="sxs-lookup"><span data-stu-id="bf515-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="bf515-123">K importu obsahu procesu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="bf515-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="bf515-124">Otevřete MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="bf515-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="bf515-125">Automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="bf515-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="bf515-126">Hostování obsahu procesu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="bf515-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="bf515-127">Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídy pro hostování daného obsahu procesu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="bf515-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="bf515-128">Pro hostování daného obsahu procesu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="bf515-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="bf515-129">V MainWindow.xaml nahraďte automaticky generované XAML následující XAML.</span><span class="sxs-lookup"><span data-stu-id="bf515-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="bf515-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="bf515-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="bf515-131">Zkopírujte knihovnu DLL, která obsahuje procesu Direct3D9 obsah do složky bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="bf515-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="bf515-132">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="bf515-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="bf515-133">Obsah procesu Direct3D9 se zobrazí v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="bf515-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf515-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf515-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="bf515-135">Otázky výkonu při procesu Direct3D9 a interoperabilita WPF</span><span class="sxs-lookup"><span data-stu-id="bf515-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
