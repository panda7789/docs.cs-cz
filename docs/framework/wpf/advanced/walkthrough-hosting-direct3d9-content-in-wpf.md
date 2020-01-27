---
title: Hostování obsahu Direct3D9 v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e65b0c59268b44abed289e54181bf0bda9355664
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742606"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="f0710-102">Návod: Hostování obsahu Direct3D9 ve WPF</span><span class="sxs-lookup"><span data-stu-id="f0710-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="f0710-103">Tento návod ukazuje, jak hostovat Direct3D9 obsah v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f0710-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="f0710-104">V tomto návodu provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="f0710-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="f0710-105">Vytvořte projekt WPF pro hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f0710-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="f0710-106">Importujte obsah Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f0710-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="f0710-107">Zobrazte obsah Direct3D9 pomocí třídy <xref:System.Windows.Interop.D3DImage>.</span><span class="sxs-lookup"><span data-stu-id="f0710-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="f0710-108">Po dokončení budete znát způsob hostování Direct3D9 obsahu v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f0710-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0710-109">Prerequisites</span></span>

<span data-ttu-id="f0710-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="f0710-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="f0710-111">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f0710-111">Visual Studio.</span></span>

- <span data-ttu-id="f0710-112">DirectX SDK 9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f0710-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="f0710-113">Knihovna DLL, která obsahuje obsah Direct3D9 ve formátu kompatibilním s WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="f0710-114">Další informace najdete v tématu spolupráce a postupy pro [WPF a Direct3D9](wpf-and-direct3d9-interoperation.md) [: vytváření obsahu Direct3D9 pro hostování v](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="f0710-115">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="f0710-115">Creating the WPF Project</span></span>

<span data-ttu-id="f0710-116">Prvním krokem je vytvoření projektu pro aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="f0710-117">Vytvoření projektu WPF</span><span class="sxs-lookup"><span data-stu-id="f0710-117">To create the WPF project</span></span>

<span data-ttu-id="f0710-118">Vytvořte nový projekt aplikace WPF v jazyce Visual C# s názvem `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="f0710-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="f0710-119">Další informace najdete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="f0710-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="f0710-120">MainWindow. XAML se otevře v Návrháři WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-120">MainWindow.xaml opens in the WPF Designer.</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="f0710-121">Import obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f0710-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="f0710-122">Obsah Direct3D9 importujete z nespravované knihovny DLL pomocí atributu `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="f0710-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="f0710-123">Import obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f0710-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="f0710-124">Otevřete MainWindow.xaml.cs v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="f0710-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="f0710-125">Nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="f0710-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="f0710-126">Hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f0710-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="f0710-127">Nakonec použijte třídu <xref:System.Windows.Interop.D3DImage> pro hostování obsahu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="f0710-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="f0710-128">Hostování obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="f0710-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="f0710-129">V souboru MainWindow. xaml nahraďte automaticky generovaný kód XAML následujícím XAML.</span><span class="sxs-lookup"><span data-stu-id="f0710-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="f0710-130">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="f0710-130">Build the project.</span></span>

3. <span data-ttu-id="f0710-131">Zkopírujte knihovnu DLL obsahující obsah Direct3D9 do složky bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="f0710-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="f0710-132">Stisknutím klávesy F5 spusťte projekt.</span><span class="sxs-lookup"><span data-stu-id="f0710-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="f0710-133">Obsah Direct3D9 se zobrazí v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="f0710-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0710-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0710-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="f0710-135">Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF</span><span class="sxs-lookup"><span data-stu-id="f0710-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
