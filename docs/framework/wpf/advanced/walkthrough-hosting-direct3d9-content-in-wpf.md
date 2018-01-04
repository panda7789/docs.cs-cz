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
ms.workload: dotnet
ms.openlocfilehash: 10558348a963f0b243dcfbe23171f6e24da6da0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Návod: Hostování obsahu Direct3D9 ve WPF
Tento návod ukazuje, jak pro hostování procesu Direct3D9 obsahu v aplikaci Windows Presentation Foundation (WPF).  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvořte projekt WPF pro hostování daného obsahu procesu Direct3D9.  
  
-   Importujte procesu Direct3D9 obsah.  
  
-   Zobrazit obsah procesu Direct3D9 pomocí <xref:System.Windows.Interop.D3DImage> třídy.  
  
 Jakmile budete hotovi, budete vědět, jak pro hostování procesu Direct3D9 obsahu v aplikaci WPF.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   DirectX SDK 9 nebo novější.  
  
-   Knihovny DLL, která obsahuje procesu Direct3D9 obsah ve formátu WPF kompatibilní. Další informace najdete v tématu [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) a [návod: vytváření obsahu procesu Direct3D9 pro hostitelský v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Vytvoření projektu WPF  
 Prvním krokem je vytvoření projektu aplikace WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Vytvoření projektu WPF  
  
-   Vytvořte nový projekt aplikace WPF v jazyce Visual C# s názvem `D3DHost`. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     Otevře se v MainWindow.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Import procesu Direct3D9 obsah  
 Importovat obsah procesu Direct3D9 z nespravovaných knihovny DLL pomocí `DllImport` atribut.  
  
#### <a name="to-import-direct3d9-content"></a>K importu obsahu procesu Direct3D9  
  
1.  Otevřete MainWindow.xaml.cs v editoru kódu.  
  
2.  Automaticky generovaného kódu nahraďte následujícím kódem.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hostování obsahu procesu Direct3D9  
 Nakonec použijte <xref:System.Windows.Interop.D3DImage> třídy pro hostování daného obsahu procesu Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Pro hostování daného obsahu procesu Direct3D9  
  
1.  V MainWindow.xaml nahraďte automaticky generované XAML následující XAML.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Sestavte projekt.  
  
3.  Zkopírujte knihovnu DLL, která obsahuje procesu Direct3D9 obsah do složky bin/Debug.  
  
4.  Stisknutím klávesy F5 spusťte projekt.  
  
     Obsah procesu Direct3D9 se zobrazí v aplikaci WPF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.D3DImage>  
 [Předpoklady výkonu pro Direct3D9 a interoperabilitu WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
