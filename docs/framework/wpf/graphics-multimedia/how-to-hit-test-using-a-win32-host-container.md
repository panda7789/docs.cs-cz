---
title: 'Postupy: Ověřování pozice pomocí kontejneru hostitele Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: ac5cae5bcd94dc8bf80ff95b8971914e1fa5ba2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081460"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Postupy: Ověřování pozice pomocí kontejneru hostitele Win32
Můžete vytvořit vizuální objekty v rámci [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okno tím, že hostitel poskytuje okno kontejneru pro vizuální objekty. Kvůli omezením vizuální objekty zpracování událostí zpracování zpráv předávaných do smyčky filtru zprávy okna kontejneru hostitele. Odkazovat na [kurzu: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) Další informace o tom, k hostování vizuální objektů v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak nastavit myš obslužné rutiny událostí pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které slouží jako kontejner hostitele pro vizuální objekty.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Následující příklad ukazuje, jak nastavit pozice v reakci na soutisku události konkrétní myši.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource> Objekt představuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsah [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] okna. Hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objekt představuje nejvyšší uzel v hierarchii vizuálního stromu.  
  
 Úplnou ukázku na přístupů testování objektů pomocí kontejneru hostitele Win32, najdete v části [spuštění testu s ukázkou vzájemná spolupráce grafického subsystému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Kurz: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
