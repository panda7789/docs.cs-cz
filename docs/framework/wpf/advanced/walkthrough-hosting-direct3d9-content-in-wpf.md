---
title: 'Návod: Hostování obsahu Direct3D9 ve WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 5e7edfbeb9a3cddcdcd81d9c87e5e85bfc947339
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188706"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="40149-102">Návod: Hostování obsahu Direct3D9 ve WPF</span><span class="sxs-lookup"><span data-stu-id="40149-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="40149-103">Tento návod ukazuje, jak k hostování obsahu Direct3D9 v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="40149-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="40149-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="40149-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="40149-105">Vytvoření projektu WPF pro hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="40149-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="40149-106">Importujte obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="40149-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="40149-107">Zobrazení obsahu Direct3D9 použitím <xref:System.Windows.Interop.D3DImage> třídy.</span><span class="sxs-lookup"><span data-stu-id="40149-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="40149-108">Až budete hotovi, budete vědět, jak k hostování obsahu Direct3D9 v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="40149-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="40149-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40149-109">Prerequisites</span></span>  
 <span data-ttu-id="40149-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="40149-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="40149-111">.</span><span class="sxs-lookup"><span data-stu-id="40149-111">.</span></span>  
  
-   <span data-ttu-id="40149-112">Rozhraní DirectX SDK 9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="40149-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="40149-113">Knihovna DLL, která obsahuje obsahu Direct3D9 ve formátu WPF kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="40149-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="40149-114">Další informace najdete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) a [návod: vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="40149-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="40149-115">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="40149-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="40149-116">Prvním krokem je vytvoření projektu pro aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="40149-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="40149-117">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="40149-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="40149-118">Vytvoření nového projektu aplikace WPF v jazyce Visual C# s názvem `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="40149-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="40149-119">Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="40149-119">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="40149-120">Otevře se v souboru MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40149-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="40149-121">Import obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="40149-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="40149-122">Import obsahu Direct3D9 z nespravovaná knihovna DLL pomocí `DllImport` atribut.</span><span class="sxs-lookup"><span data-stu-id="40149-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="40149-123">K importu obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="40149-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="40149-124">Otevřete soubor MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="40149-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="40149-125">Automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="40149-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="40149-126">Hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="40149-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="40149-127">Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídy k hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="40149-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="40149-128">K hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="40149-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="40149-129">V souboru MainWindow.xaml nahraďte automaticky generované XAML následující XAML.</span><span class="sxs-lookup"><span data-stu-id="40149-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="40149-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="40149-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="40149-131">Kopírovat knihovnu DLL, která obsahuje obsahu Direct3D9 do složky bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="40149-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="40149-132">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="40149-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="40149-133">Obsahu Direct3D9 se zobrazí v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="40149-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40149-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="40149-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="40149-135">Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF</span><span class="sxs-lookup"><span data-stu-id="40149-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
