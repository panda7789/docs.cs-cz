---
title: 'Návod: Vytvoření obsahu Direct3D9 pro hostování ve WPF'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 160395b84ef7ca447d162ceff34752113a1d59a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031197"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Návod: Vytvoření obsahu Direct3D9 pro hostování ve WPF
Tento návod ukazuje, jak k vytvoření obsahu Direct3D9, který je vhodný pro hostování v aplikaci Windows Presentation Foundation (WPF). Další informace o hostování obsahu Direct3D9 v aplikaci WPF, naleznete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](wpf-and-direct3d9-interoperation.md).

 V tomto podrobném návodu můžete provádět následující úlohy:

- Vytvořte projekt Direct3D9.

- Konfigurace projektu Direct3D9 pro hostování v aplikaci WPF.

 Až budete hotovi, budete mít knihovnu DLL, která obsahuje obsahu Direct3D9 pro použití v aplikaci WPF.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2010.

- Rozhraní DirectX SDK 9 nebo novější.

## <a name="creating-the-direct3d9-project"></a>Vytvoření projektu Direct3D9
 Prvním krokem je vytvoření a konfigurace projektu Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Chcete-li vytvořit projekt Direct3D9

1. Vytvořte nový projekt Win32 v jazyce C++ s názvem `D3DContent`.

     Průvodce aplikací Win32 otevře a zobrazí se úvodní obrazovka.

2. Klikněte na **Další**.

     Obrazovka nastavení aplikace se zobrazí.

3. V **typ aplikace:** vyberte **DLL** možnost.

4. Klikněte na tlačítko **Dokončit**.

     Je generována D3DContent projektu.

5. V Průzkumníku řešení klikněte pravým tlačítkem na projekt D3DContent a vyberte **vlastnosti**.

     **Stránky vlastností D3DContent** zobrazí se dialogové okno.

6. Vyberte **C/C++** uzlu.

7. V **další adresáře souborů k zahrnutí** zadejte umístění DirectX zahrnují složku. Výchozí umístění pro tuto složku nachází v %ProgramFiles%\Microsoft rozhraní DirectX SDK (*verze*) \Include.

8. Dvakrát klikněte **Linkeru** uzel a rozbalte ho.

9. V **další adresáře knihoven** zadejte umístění složky knihovny rozhraní DirectX. Výchozí umístění pro tuto složku nachází v %ProgramFiles%\Microsoft rozhraní DirectX SDK (*verze*) \Lib\x86.

10. Vyberte **vstup** uzlu.

11. V **Další závislosti** pole, přidat `d3d9.lib` a `d3dx9.lib` soubory.

12. V Průzkumníku řešení, přidejte nový modul soubor definice (.def) s názvem `D3DContent.def` do projektu.

## <a name="creating-the-direct3d9-content"></a>Vytvoření obsahu Direct3D9
 Pokud chcete získat nejlepší výkon, musíte použít obsahu Direct3D9 konkrétní nastavení. Následující kód ukazuje, jak vytvořit Direct3D9 povrch, který je nejlepší výkonové charakteristiky. Další informace najdete v tématu [důležité informace o výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>K vytvoření obsahu Direct3D9

1. Tři třídy jazyka C++ pomocí Průzkumníka řešení, přidejte do projektu s tímto názvem.

     `CRenderer` (s virtuální destruktor)

     `CRendererManager`

     `CTriangleRenderer`

2. Otevřete Renderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. Otevřete Renderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. Otevřete RendererManager.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. Otevřete RendererManager.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. Otevřete TriangleRenderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. Otevřete TriangleRenderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. Stdafx.h otevřete v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Dllmain.cpp otevřete v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Otevřete D3DContent.def v editoru kódu.

11. Automaticky generovaného kódu nahraďte následujícím kódem.

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

12. Sestavte projekt.

## <a name="next-steps"></a>Další kroky

- Hostování obsahu Direct3D9 v aplikaci WPF. Další informace najdete v tématu [názorný postup: Hostování obsahu Direct3D9 v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Návod: Hostování obsahu Direct3D9 v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
