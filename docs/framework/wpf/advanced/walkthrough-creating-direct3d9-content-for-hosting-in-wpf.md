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
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF
Tento návod ukazuje, jak vytvořit Direct3D9 obsah, který je vhodný pro hostování v aplikaci Windows Presentation Foundation (WPF). Další informace o hostování Direct3D9 obsahu v aplikacích WPF najdete v tématu [spolupráce WPF a Direct3D9](wpf-and-direct3d9-interoperation.md).

 V tomto návodu provedete následující úlohy:

- Vytvořte projekt Direct3D9.

- Nakonfigurujte projekt Direct3D9 pro hostování v aplikaci WPF.

 Po dokončení budete mít knihovnu DLL, která obsahuje obsah Direct3D9 pro použití v aplikaci WPF.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2010.

- DirectX SDK 9 nebo novější.

## <a name="creating-the-direct3d9-project"></a>Vytvoření projektu Direct3D9
 Prvním krokem je vytvoření a konfigurace projektu Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Vytvoření projektu Direct3D9

1. Vytvořte nový projekt Win32 v C++ pojmenovaném `D3DContent`.

     Otevře se Průvodce aplikací Win32 a zobrazí se uvítací obrazovka.

2. Klikněte na **Další**.

     Zobrazí se obrazovka nastavení aplikace.

3. V části **Typ aplikace:** vyberte možnost **DLL** .

4. Klikněte na **Dokončit**.

     Vygeneruje se projekt D3DContent.

5. V Průzkumník řešení klikněte pravým tlačítkem na projekt D3DContent a vyberte **vlastnosti**.

     Otevře se dialogové okno **stránky vlastností D3DContent** .

6. Vyberte uzel **C/C++**  uzel.

7. Do pole **Další adresáře k zahrnutí** zadejte umístění složky pro zahrnutí rozhraní DirectX. Výchozím umístěním pro tuto složku je%ProgramFiles%\Microsoft DirectX SDK (*verze*) \Include.

8. Poklikejte na uzel **linkeru** a rozbalte ho.

9. V poli **Další adresáře knihoven** zadejte umístění složky knihovny DirectX. Výchozím umístěním pro tuto složku je%ProgramFiles%\Microsoft DirectX SDK (*verze*) \Lib\x86.

10. Vyberte **vstupní** uzel.

11. Do pole **Další závislosti** přidejte `d3d9.lib` a soubory `d3dx9.lib`.

12. V Průzkumník řešení přidejte do projektu nový soubor definice modulu (. def) s názvem `D3DContent.def`.

## <a name="creating-the-direct3d9-content"></a>Vytváření obsahu Direct3D9
 Aby se dosáhlo co nejlepšího výkonu, váš obsah Direct3D9 musí používat konkrétní nastavení. Následující kód ukazuje, jak vytvořit Direct3D9 plochu, která má nejlepší výkonnostní charakteristiky. Další informace najdete v tématu [požadavky na výkon pro interoperabilitu Direct3D9 a WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Vytvoření obsahu Direct3D9

1. Pomocí Průzkumník řešení přidejte do projektu C++ tři třídy s názvem následující.

     `CRenderer` (s virtuálním destruktorem)

     `CRendererManager`

     `CTriangleRenderer`

2. Otevřete modul pro vykreslování. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. Otevřete nástroj pro vykreslování. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. Otevřete RendererManager. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. Otevřete RendererManager. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. Otevřete TriangleRenderer. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. Otevřete TriangleRenderer. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. Otevřete soubor stdafx. h v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Otevřete DllMain. cpp v editoru kódu a nahraďte automaticky generovaný kód následujícím kódem.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Otevřete D3DContent. def v editoru kódu.

11. Nahraďte automaticky generovaný kód následujícím kódem.

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

12. Sestavte projekt.

## <a name="next-steps"></a>Další kroky

- Hostování obsahu Direct3D9 v aplikaci WPF. Další informace najdete v tématu [Návod: hostování Direct3D9 obsahu v](walkthrough-hosting-direct3d9-content-in-wpf.md)subsystému WPF.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.D3DImage>
- [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Návod: Hostování obsahu Direct3D9 v subsystému WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
