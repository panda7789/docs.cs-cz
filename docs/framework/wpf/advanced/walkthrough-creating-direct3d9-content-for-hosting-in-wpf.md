---
title: Vytvoření obsahu Direct3D9 pro hostování
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 847ee74da5b295c2c9d3824b3df74f94bc98a4db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727914"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="5fb6c-102">Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF</span><span class="sxs-lookup"><span data-stu-id="5fb6c-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="5fb6c-103">Tento návod ukazuje, jak vytvořit Direct3D9 obsah, který je vhodný pro hostování v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5fb6c-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="5fb6c-104">Další informace o hostování Direct3D9 obsahu v aplikacích WPF najdete v tématu [spolupráce WPF a Direct3D9](wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="5fb6c-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="5fb6c-105">V tomto návodu provedete následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="5fb6c-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="5fb6c-106">Vytvořte projekt Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-106">Create a Direct3D9 project.</span></span>

- <span data-ttu-id="5fb6c-107">Nakonfigurujte projekt Direct3D9 pro hostování v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="5fb6c-108">Po dokončení budete mít knihovnu DLL, která obsahuje obsah Direct3D9 pro použití v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fb6c-109">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="5fb6c-109">Prerequisites</span></span>
 <span data-ttu-id="5fb6c-110">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="5fb6c-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="5fb6c-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-111">Visual Studio 2010.</span></span>

- <span data-ttu-id="5fb6c-112">DirectX SDK 9 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-112">DirectX SDK 9 or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="5fb6c-113">Vytvoření projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="5fb6c-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="5fb6c-114">Prvním krokem je vytvoření a konfigurace projektu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="5fb6c-115">Vytvoření projektu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="5fb6c-115">To create the Direct3D9 project</span></span>

1. <span data-ttu-id="5fb6c-116">Vytvořte nový projekt Win32 v C++ pojmenovaném `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="5fb6c-117">Otevře se Průvodce aplikací Win32 a zobrazí se uvítací obrazovka.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2. <span data-ttu-id="5fb6c-118">Klikněte na **Další**.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-118">Click **Next**.</span></span>

     <span data-ttu-id="5fb6c-119">Zobrazí se obrazovka nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-119">The Application Settings screen appears.</span></span>

3. <span data-ttu-id="5fb6c-120">V části **Typ aplikace:** vyberte možnost **DLL** .</span><span class="sxs-lookup"><span data-stu-id="5fb6c-120">In the **Application type:** section, select the **DLL** option.</span></span>

4. <span data-ttu-id="5fb6c-121">Klikněte na **Finish** (Dokončit).</span><span class="sxs-lookup"><span data-stu-id="5fb6c-121">Click **Finish**.</span></span>

     <span data-ttu-id="5fb6c-122">Vygeneruje se projekt D3DContent.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-122">The D3DContent project is generated.</span></span>

5. <span data-ttu-id="5fb6c-123">V Průzkumník řešení klikněte pravým tlačítkem na projekt D3DContent a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="5fb6c-124">Otevře se dialogové okno **stránky vlastností D3DContent** .</span><span class="sxs-lookup"><span data-stu-id="5fb6c-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6. <span data-ttu-id="5fb6c-125">Vyberte uzel **C/C++**  uzel.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-125">Select the **C/C++** node.</span></span>

7. <span data-ttu-id="5fb6c-126">Do pole **Další adresáře k zahrnutí** zadejte umístění složky pro zahrnutí rozhraní DirectX.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="5fb6c-127">Výchozím umístěním pro tuto složku je%ProgramFiles%\Microsoft DirectX SDK (*verze*) \Include.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8. <span data-ttu-id="5fb6c-128">Poklikejte na uzel **linkeru** a rozbalte ho.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="5fb6c-129">V poli **Další adresáře knihoven** zadejte umístění složky knihovny DirectX.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="5fb6c-130">Výchozím umístěním pro tuto složku je%ProgramFiles%\Microsoft DirectX SDK (*verze*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="5fb6c-131">Vyberte **vstupní** uzel.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="5fb6c-132">Do pole **Další závislosti** přidejte `d3d9.lib` a soubory `d3dx9.lib`.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="5fb6c-133">V Průzkumník řešení přidejte do projektu nový soubor definice modulu (. def) s názvem `D3DContent.def`.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="5fb6c-134">Vytváření obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="5fb6c-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="5fb6c-135">Aby se dosáhlo co nejlepšího výkonu, váš obsah Direct3D9 musí používat konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="5fb6c-136">Následující kód ukazuje, jak vytvořit Direct3D9 plochu, která má nejlepší výkonnostní charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="5fb6c-137">Další informace najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="5fb6c-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="5fb6c-138">Vytvoření obsahu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="5fb6c-138">To create the Direct3D9 content</span></span>

1. <span data-ttu-id="5fb6c-139">Pomocí Průzkumník řešení přidejte do projektu C++ tři třídy s názvem následující.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="5fb6c-140">`CRenderer` (s virtuálním destruktorem)</span><span class="sxs-lookup"><span data-stu-id="5fb6c-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2. <span data-ttu-id="5fb6c-141">Otevřete modul pro vykreslování. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. <span data-ttu-id="5fb6c-142">Otevřete nástroj pro vykreslování. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. <span data-ttu-id="5fb6c-143">Otevřete RendererManager. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. <span data-ttu-id="5fb6c-144">Otevřete RendererManager. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. <span data-ttu-id="5fb6c-145">Otevřete TriangleRenderer. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. <span data-ttu-id="5fb6c-146">Otevřete TriangleRenderer. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. <span data-ttu-id="5fb6c-147">Otevřete soubor stdafx. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="5fb6c-148">Otevřete DllMain. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="5fb6c-149">Otevřete D3DContent. def v editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="5fb6c-150">Nahraďte automaticky generovaný kód následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-150">Replace the automatically generated code with the following code.</span></span>

    ```cpp
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

12. <span data-ttu-id="5fb6c-151">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5fb6c-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5fb6c-152">Next Steps</span></span>

- <span data-ttu-id="5fb6c-153">Hostování obsahu Direct3D9 v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="5fb6c-154">Další informace najdete v tématu [Návod: hostování Direct3D9 obsahu v](walkthrough-hosting-direct3d9-content-in-wpf.md)subsystému WPF.</span><span class="sxs-lookup"><span data-stu-id="5fb6c-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb6c-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fb6c-155">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="5fb6c-156">Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF</span><span class="sxs-lookup"><span data-stu-id="5fb6c-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="5fb6c-157">Návod: Hostování obsahu Direct3D9 v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="5fb6c-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](walkthrough-hosting-direct3d9-content-in-wpf.md)
