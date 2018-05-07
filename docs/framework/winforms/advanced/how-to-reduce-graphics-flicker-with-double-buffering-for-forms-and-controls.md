---
title: 'Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: 6e11e364af5dc361a24cdd88d72432d6ba4d4058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky
Chcete-li vyřešit blikání problémy spojené s více operací Malování dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti. Pokud dvojité ukládání do vyrovnávací paměti je povoleno, všechny operace Malování vykresleny nejprve do vyrovnávací paměti místo kreslicí plochy na obrazovce. Po dokončení všech operací Malování vyrovnávací paměť je zkopírovat přímo do kreslicí plochy s ním spojená. Vzhledem k tomu, že pouze jeden grafické operace na obrazovce, blikání bitové kopie přidružený komplexní vykreslovací operace odstranění. Pro většinu aplikací, výchozí dvojité ukládání do vyrovnávací paměti zajišťuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bude poskytovat nejlepší výsledky. Standardní ovládací prvky Windows Forms jsou dvojité vyrovnávací paměti ve výchozím nastavení. Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti do svých formulářů a vytvořené ovládací prvky dvěma způsoby. Můžete buď sadu <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`, nebo můžete volat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu a nastavit <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`. Obě metody povolí, výchozí dvojité ukládání do vyrovnávací paměti pro formuláře nebo ovládacího prvku a poskytují blikání grafiky vykreslování. Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metoda se doporučuje jenom pro vlastní ovládací prvky, pro které jste napsali všechny kód vykreslování.  
  
 Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo Správa rozšířené paměti můžete implementovat vlastní logiky dvojité vyrovnávací paměti. Další informace najdete v tématu [postupy: ruční správa grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Ke snížení blikání  
  
-   Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- nebo –  
  
-   Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metodu a nastavit <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [Grafiky s dvojitou vyrovnávací pamětí](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
