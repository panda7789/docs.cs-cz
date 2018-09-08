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
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Návod: Hostování obsahu Direct3D9 ve WPF
Tento návod ukazuje, jak k hostování obsahu Direct3D9 v aplikaci Windows Presentation Foundation (WPF).  
  
 V tomto podrobném návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu WPF pro hostování obsahu Direct3D9.  
  
-   Importujte obsahu Direct3D9.  
  
-   Zobrazení obsahu Direct3D9 použitím <xref:System.Windows.Interop.D3DImage> třídy.  
  
 Až budete hotovi, budete vědět, jak k hostování obsahu Direct3D9 v aplikaci WPF.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Rozhraní DirectX SDK 9 nebo novější.  
  
-   Knihovna DLL, která obsahuje obsahu Direct3D9 ve formátu WPF kompatibilní. Další informace najdete v tématu [WPF a systému Direct3D9 vzájemná spolupráce grafického subsystému](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) a [návod: vytvoření obsahu Direct3D9 pro hostování v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Vytvoření projektu WPF  
 Prvním krokem je vytvoření projektu pro aplikaci WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF  
  
-   Vytvoření nového projektu aplikace WPF v jazyce Visual C# s názvem `D3DHost`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     Otevře se v souboru MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Import obsahu Direct3D9  
 Import obsahu Direct3D9 z nespravovaná knihovna DLL pomocí `DllImport` atribut.  
  
#### <a name="to-import-direct3d9-content"></a>K importu obsahu Direct3D9  
  
1.  Otevřete soubor MainWindow.xaml.cs v editoru kódu.  
  
2.  Automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hostování obsahu Direct3D9  
 Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídy k hostování obsahu Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>K hostování obsahu Direct3D9  
  
1.  V souboru MainWindow.xaml nahraďte automaticky generované XAML následující XAML.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Sestavte projekt.  
  
3.  Kopírovat knihovnu DLL, která obsahuje obsahu Direct3D9 do složky bin/Debug.  
  
4.  Stisknutím klávesy F5 spusťte projekt.  
  
     Obsahu Direct3D9 se zobrazí v aplikaci WPF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.D3DImage>  
 [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
