---
title: 'Postupy: Spuštění testu použitím kontejneru hostitele Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452802"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Postupy: Spuštění testu použitím kontejneru hostitele Win32
Můžete vytvořit vizuální objekty v okně Win32 tím, že poskytnete kontejner hostitelského okna pro vizuální objekty. Chcete-li zajistit zpracování událostí pro obsažené vizuální objekty, které zpracovávají zprávy předané do smyčky filtru zpráv kontejneru hostitelského okna. Další informace o tom, jak hostovat vizuální objekty v okně Win32, najdete [v tématu Kurz: hostování vizuálních objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) .  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak nastavit obslužné rutiny událostí myši pro okno Win32, které se používá jako kontejner hostitele pro vizuální objekty.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 Následující příklad ukazuje, jak nastavit test přístupů v reakci na přesahy konkrétních událostí myši.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Objekt <xref:System.Windows.Interop.HwndSource> prezentuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu v rámci okna Win32. Hodnota vlastnosti <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource> představuje uzel nejvyšší úrovně v hierarchii vizuálního stromu.  
  
 Kompletní ukázku pro testování objektů pomocí kontejneru hostitele Win32 naleznete v tématu [test volání s ukázkovou meziprovozu](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)Win32.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndSource>
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Kurz: Hostování vizuální objektů v aplikaci Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
