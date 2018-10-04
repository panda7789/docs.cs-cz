---
title: 'Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 321c4ba8659bd2226fff96e74e81ef24f0077c3d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48580953"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="eddb9-102">Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF</span><span class="sxs-lookup"><span data-stu-id="eddb9-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="eddb9-103">Tento návod ukazuje, jak k vytvoření obsahu Direct3D9, který je vhodný pro hostování v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="eddb9-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="eddb9-104">Další informace o hostování obsahu Direct3D9 v aplikaci WPF, naleznete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="eddb9-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="eddb9-105">V tomto podrobném návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="eddb9-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="eddb9-106">Vytvořte projekt Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="eddb9-106">Create a Direct3D9 project.</span></span>

-   <span data-ttu-id="eddb9-107">Konfigurace projektu Direct3D9 pro hostování v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="eddb9-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="eddb9-108">Až budete hotovi, budete mít knihovnu DLL, která obsahuje obsahu Direct3D9 pro použití v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="eddb9-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eddb9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eddb9-109">Prerequisites</span></span>
 <span data-ttu-id="eddb9-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="eddb9-110">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="eddb9-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="eddb9-111">Visual Studio 2010.</span></span>

-   <span data-ttu-id="eddb9-112">Rozhraní DirectX SDK 9or později.</span><span class="sxs-lookup"><span data-stu-id="eddb9-112">DirectX SDK 9or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="eddb9-113">Vytvoření projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="eddb9-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="eddb9-114">Prvním krokem je vytvoření a konfigurace projektu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="eddb9-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="eddb9-115">Chcete-li vytvořit projekt Direct3D9</span><span class="sxs-lookup"><span data-stu-id="eddb9-115">To create the Direct3D9 project</span></span>

1.  <span data-ttu-id="eddb9-116">Vytvořte nový projekt Win32 v jazyce C++ s názvem `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="eddb9-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="eddb9-117">Průvodce aplikací Win32 otevře a zobrazí se úvodní obrazovka.</span><span class="sxs-lookup"><span data-stu-id="eddb9-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2.  <span data-ttu-id="eddb9-118">Klikněte na tlačítko **Další**.</span><span class="sxs-lookup"><span data-stu-id="eddb9-118">Click **Next**.</span></span>

     <span data-ttu-id="eddb9-119">Obrazovka nastavení aplikace se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="eddb9-119">The Application Settings screen appears.</span></span>

3.  <span data-ttu-id="eddb9-120">V **typ aplikace:** vyberte **DLL** možnost.</span><span class="sxs-lookup"><span data-stu-id="eddb9-120">In the **Application type:** section, select the **DLL** option.</span></span>

4.  <span data-ttu-id="eddb9-121">Klikněte na tlačítko **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="eddb9-121">Click **Finish**.</span></span>

     <span data-ttu-id="eddb9-122">Je generována D3DContent projektu.</span><span class="sxs-lookup"><span data-stu-id="eddb9-122">The D3DContent project is generated.</span></span>

5.  <span data-ttu-id="eddb9-123">V Průzkumníku řešení klikněte pravým tlačítkem na projekt D3DContent a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="eddb9-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="eddb9-124">**Stránky vlastností D3DContent** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="eddb9-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6.  <span data-ttu-id="eddb9-125">Vyberte **C/C++** uzlu.</span><span class="sxs-lookup"><span data-stu-id="eddb9-125">Select the **C/C++** node.</span></span>

7.  <span data-ttu-id="eddb9-126">V **další adresáře souborů k zahrnutí** zadejte umístění DirectX zahrnují složku.</span><span class="sxs-lookup"><span data-stu-id="eddb9-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="eddb9-127">Výchozí umístění pro tuto složku nachází v %ProgramFiles%\Microsoft rozhraní DirectX SDK (*verze*) \Include.</span><span class="sxs-lookup"><span data-stu-id="eddb9-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8.  <span data-ttu-id="eddb9-128">Dvakrát klikněte **Linkeru** uzel a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="eddb9-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="eddb9-129">V **další adresáře knihoven** zadejte umístění složky knihovny rozhraní DirectX.</span><span class="sxs-lookup"><span data-stu-id="eddb9-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="eddb9-130">Výchozí umístění pro tuto složku nachází v %ProgramFiles%\Microsoft rozhraní DirectX SDK (*verze*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="eddb9-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="eddb9-131">Vyberte **vstup** uzlu.</span><span class="sxs-lookup"><span data-stu-id="eddb9-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="eddb9-132">V **Další závislosti** pole, přidat `d3d9.lib` a `d3dx9.lib` soubory.</span><span class="sxs-lookup"><span data-stu-id="eddb9-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="eddb9-133">V Průzkumníku řešení, přidejte nový modul soubor definice (.def) s názvem `D3DContent.def` do projektu.</span><span class="sxs-lookup"><span data-stu-id="eddb9-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="eddb9-134">Vytvoření obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="eddb9-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="eddb9-135">Pokud chcete získat nejlepší výkon, musíte použít obsahu Direct3D9 konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="eddb9-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="eddb9-136">Následující kód ukazuje, jak vytvořit Direct3D9 povrch, který je nejlepší výkonové charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="eddb9-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="eddb9-137">Další informace najdete v tématu [důležité informace o výkonu pro Direct3D9 a interoperabilitu WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="eddb9-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="eddb9-138">K vytvoření obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="eddb9-138">To create the Direct3D9 content</span></span>

1.  <span data-ttu-id="eddb9-139">Tři třídy jazyka C++ pomocí Průzkumníka řešení, přidejte do projektu s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="eddb9-140">`CRenderer` (s virtuální destruktor)</span><span class="sxs-lookup"><span data-stu-id="eddb9-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2.  <span data-ttu-id="eddb9-141">Otevřete Renderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  <span data-ttu-id="eddb9-142">Otevřete Renderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  <span data-ttu-id="eddb9-143">Otevřete RendererManager.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  <span data-ttu-id="eddb9-144">Otevřete RendererManager.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  <span data-ttu-id="eddb9-145">Otevřete TriangleRenderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  <span data-ttu-id="eddb9-146">Otevřete TriangleRenderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  <span data-ttu-id="eddb9-147">Stdafx.h otevřete v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="eddb9-148">Dllmain.cpp otevřete v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="eddb9-149">Otevřete D3DContent.def v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="eddb9-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="eddb9-150">Automaticky generovaného kódu nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="eddb9-150">Replace the automatically generated code with the following code.</span></span>

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. <span data-ttu-id="eddb9-151">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="eddb9-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="eddb9-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="eddb9-152">Next Steps</span></span>

-   <span data-ttu-id="eddb9-153">Hostování obsahu Direct3D9 v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="eddb9-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="eddb9-154">Další informace najdete v tématu [návod: hostování obsahu Direct3D9 v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="eddb9-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eddb9-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="eddb9-155">See Also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="eddb9-156">Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF</span><span class="sxs-lookup"><span data-stu-id="eddb9-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="eddb9-157">Návod: Hostování obsahu Direct3D9 v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="eddb9-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)