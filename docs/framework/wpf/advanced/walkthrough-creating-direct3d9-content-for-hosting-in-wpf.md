---
title: "Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1a5d70807541a0a3faf6bc99a3ced42827efd72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Návod: Vytvoření obsahu Direct3D9 pro hostování v objektu WPF
Tento návod ukazuje postup vytvoření procesu Direct3D9 obsah, který je vhodný pro hostování v aplikaci Windows Presentation Foundation (WPF). Další informace o hostování procesu Direct3D9 obsahu v aplikaci WPF najdete v tématu [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření procesu Direct3D9 projektu.  
  
-   Konfigurace projektu procesu Direct3D9 pro hostování v aplikaci WPF.  
  
 Jakmile budete hotovi, budete mít knihovny DLL, která obsahuje procesu Direct3D9 obsah pro použití v aplikaci WPF.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Později 9or DirectX SDK.  
  
## <a name="creating-the-direct3d9-project"></a>Vytvoření projektu procesu Direct3D9  
 Prvním krokem je vytvoření a konfigurace procesu Direct3D9 projektu.  
  
#### <a name="to-create-the-direct3d9-project"></a>K vytvoření procesu Direct3D9 projektu  
  
1.  Vytvoření nového projektu Win32 v jazyce C++ s názvem `D3DContent`.  
  
     Průvodce aplikací Win32 se zobrazí na úvodní obrazovce.  
  
2.  Klikněte na tlačítko **Další**.  
  
     Zobrazí se obrazovka nastavení aplikace.  
  
3.  V **typ aplikace:** vyberte **DLL** možnost.  
  
4.  Klikněte na tlačítko **Dokončit**.  
  
     Generuje se D3DContent projektu.  
  
5.  V Průzkumníku řešení klikněte pravým tlačítkem na projekt D3DContent a vyberte **vlastnosti**.  
  
     **Stránky vlastností D3DContent** otevře se dialogové okno.  
  
6.  Vyberte **C/C++** uzlu.  
  
7.  V **další adresáře Include** pole, zadejte umístění DirectX zahrnují složku. Výchozí umístění této složky je %ProgramFiles%\Microsoft SDK rozhraní DirectX (*verze*) \Include.  
  
8.  Dvakrát klikněte **Linkeru** uzel a rozbalte ji.  
  
9. V **další adresáře knihovny** pole, zadejte umístění složky knihovny DirectX. Výchozí umístění této složky je %ProgramFiles%\Microsoft SDK rozhraní DirectX (*verze*) \Lib\x86.  
  
10. Vyberte **vstup** uzlu.  
  
11. V **Další závislosti** pole, přidejte `d3d9.lib` a `d3dx9.lib` soubory.  
  
12. V Průzkumníku řešení, přidejte nové definice souboru modulu (.def) s názvem `D3DContent.def` do projektu.  
  
## <a name="creating-the-direct3d9-content"></a>Vytvoření procesu Direct3D9 obsah  
 Získat nejlepší výkon, musíte použít svůj obsah procesu Direct3D9 konkrétní položky nastavení. Následující kód ukazuje, jak vytvořit procesu Direct3D9 prostor, který má nejlepší výkonové charakteristiky. Další informace najdete v tématu [otázky výkonu při procesu Direct3D9 a interoperabilita WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
#### <a name="to-create-the-direct3d9-content"></a>Chcete-li vytvořit procesu Direct3D9 obsahu  
  
1.  Tři třídy jazyka C++ pomocí Průzkumníka řešení, přidejte do projektu s názvem následující.  
  
     `CRenderer`(s virtuální destruktor)  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  Otevřete Renderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  Otevřete Renderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  Otevřete RendererManager.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  Otevřete RendererManager.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  Otevřete TriangleRenderer.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  Otevřete TriangleRenderer.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  Otevřete stdafx.h v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. Otevřete dllmain.cpp v editoru kódu a automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
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
  
-   Hostování obsahu procesu Direct3D9 v aplikaci WPF. Další informace najdete v tématu [návod: hostování obsahu procesu Direct3D9 v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.D3DImage>  
 [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Návod: Hostování obsahu Direct3D9 v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
