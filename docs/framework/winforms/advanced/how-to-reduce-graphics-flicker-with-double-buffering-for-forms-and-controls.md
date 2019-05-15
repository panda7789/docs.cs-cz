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
ms.openlocfilehash: d143d7ec87a214a900264e069b329ea28a92c3e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590378"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky
K vyřešení blikání problémy související s více operací malířského dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti. Pokud dvojité ukládání do vyrovnávací paměti je povolená, všechny operace Malování vykresleny nejprve do vyrovnávací paměti namísto na návrhovém povrchu na obrazovce. Po dokončení všechny operace Malování vyrovnávací paměť je zkopírován přímo do na návrhovém povrchu s ním spojená. Protože pouze jediného grafického operace se provádí na obrazovce, image blikání spojené s operacemi komplexní Malování se odstraní. Pro většinu aplikací výchozí dvojité ukládání do vyrovnávací paměti rozhraní .NET Framework poskytuje poskytne nejlepší výsledky. Standardní ovládací prvky Windows Forms jsou dvojité vyrovnávací paměti ve výchozím nastavení. Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti do svých formulářů a je také autorem ovládací prvky dvěma způsoby. Můžete buď nastaven <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`, nebo můžete volat <xref:System.Windows.Forms.Control.SetStyle%2A> metody nastavte <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`. Obě metody povolí výchozí dvojité ukládání do vyrovnávací paměti pro formuláře nebo ovládacího prvku a zadejte vykreslování bez blikání grafiky. Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metoda se doporučuje jenom pro vlastní ovládací prvky, pro které jste napsali v kódu vykreslování.  
  
 Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo rozšířené paměti pro správu můžete implementovat vlastní logiku dvojité vyrovnávací paměti. Další informace najdete v tématu [jak: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md).  
  
### <a name="to-reduce-flicker"></a>Abyste snížili blikání  
  
- Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- nebo –  
  
- Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metody nastavte <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak `true`.  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [Grafiky s dvojitou vyrovnávací pamětí](double-buffered-graphics.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
