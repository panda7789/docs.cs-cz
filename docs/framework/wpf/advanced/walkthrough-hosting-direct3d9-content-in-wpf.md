---
title: 'Návod: Hostování obsahu Direct3D9 ve WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: 90d0c578c6797342c667f16afdb523b1b4ad6685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145909"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="55370-102">Návod: Hostování obsahu Direct3D9 ve WPF</span><span class="sxs-lookup"><span data-stu-id="55370-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="55370-103">Tento návod ukazuje, jak k hostování obsahu Direct3D9 v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="55370-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="55370-104">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="55370-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="55370-105">Vytvoření projektu WPF pro hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="55370-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="55370-106">Importujte obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="55370-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="55370-107">Zobrazení obsahu Direct3D9 použitím <xref:System.Windows.Interop.D3DImage> třídy.</span><span class="sxs-lookup"><span data-stu-id="55370-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="55370-108">Až budete hotovi, budete vědět, jak k hostování obsahu Direct3D9 v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="55370-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55370-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55370-109">Prerequisites</span></span>  
 <span data-ttu-id="55370-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="55370-110">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="55370-111">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55370-111">Visual Studio.</span></span>  
  
-   <span data-ttu-id="55370-112">Rozhraní DirectX SDK 9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="55370-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="55370-113">Knihovna DLL, která obsahuje obsahu Direct3D9 ve formátu WPF kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="55370-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="55370-114">Další informace najdete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](wpf-and-direct3d9-interoperation.md) a [názorný postup: Vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="55370-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="55370-115">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="55370-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="55370-116">Prvním krokem je vytvoření projektu pro aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="55370-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="55370-117">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="55370-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="55370-118">Vytvoření nového projektu aplikace WPF v jazyce Visual C# s názvem `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="55370-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="55370-119">Další informace najdete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="55370-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
     <span data-ttu-id="55370-120">Otevře se v souboru MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55370-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="55370-121">Import obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="55370-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="55370-122">Import obsahu Direct3D9 z nespravovaná knihovna DLL pomocí `DllImport` atribut.</span><span class="sxs-lookup"><span data-stu-id="55370-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="55370-123">K importu obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="55370-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="55370-124">Otevřete soubor MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="55370-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="55370-125">Automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="55370-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="55370-126">Hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="55370-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="55370-127">Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídy k hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="55370-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="55370-128">K hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="55370-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="55370-129">V souboru MainWindow.xaml nahraďte automaticky generované XAML následující XAML.</span><span class="sxs-lookup"><span data-stu-id="55370-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="55370-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="55370-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="55370-131">Kopírovat knihovnu DLL, která obsahuje obsahu Direct3D9 do složky bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="55370-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="55370-132">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="55370-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="55370-133">Obsahu Direct3D9 se zobrazí v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="55370-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55370-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55370-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="55370-135">Předpokládaný výkon pro Direct3D9 a interoperabilitu WPF</span><span class="sxs-lookup"><span data-stu-id="55370-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
