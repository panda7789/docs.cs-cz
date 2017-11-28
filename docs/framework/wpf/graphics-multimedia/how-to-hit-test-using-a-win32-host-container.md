---
title: "Postupy: Spuštění testu použitím kontejneru hostitele Win32"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5cb77a53cbb106593b70d618bab67ef816e901
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Postupy: Spuštění testu použitím kontejneru hostitele Win32
Můžete vytvořit vizuální objekty v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno tím, že hostitel poskytuje okno kontejner pro vizuální objekty. Zajistit pro obsažené objekty visual zpracování událostí při zpracování zpráv předávaných do kontejneru okno hostitele smyčka filtru zpráv. Odkazovat na [kurz: hostování vizuální objekty v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) Další informace o tom, jak hostovat vizuální objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak nastavit myši obslužných rutin událostí pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které slouží jako kontejner hostitele pro vizuální objekty.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Následující příklad ukazuje, jak nastavit přístupů testu v reakci na soutisku události konkrétní myši.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Objekt uvede [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno. Hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objekt představuje nejvyšší uzel v hierarchii vizuálním stromu.  
  
 Je kompletní ukázka přístupů testování objekty pomocí kontejner Win32 hostitele, najdete v části [stiskněte tlačítko Test s ukázkou vzájemná spolupráce Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndSource>  
 [Ve Visual vrstvě testování průchodu](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Kurz: Hostování vizuální objekty v aplikaci Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
