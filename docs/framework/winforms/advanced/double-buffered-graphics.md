---
title: Grafiky s dvojitou vyrovnávací pamětí
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: 20ec03e6b84110f7ea00c134dc18b23f233c5f58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103438"
---
# <a name="double-buffered-graphics"></a>Grafiky s dvojitou vyrovnávací pamětí
Blikání je běžný problém při programování grafiky. Grafické operace, které vyžadují více komplexní Malování operací může způsobit vykresleného obrázku do blikat nebo v opačném případě nepřijatelné vzhled. K řešení těchto problémů, rozhraní .NET Framework poskytuje přístup k dvojité ukládání do vyrovnávací paměti.  
  
 K vyřešení blikání problémy související s více operací malířského dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti. Pokud dvojité ukládání do vyrovnávací paměti je povolená, všechny operace Malování vykresleny nejprve do vyrovnávací paměti namísto na návrhovém povrchu na obrazovce. Po dokončení všechny operace Malování vyrovnávací paměť je zkopírován přímo do na návrhovém povrchu s ním spojená. Protože pouze jediného grafického operace se provádí na obrazovce, image blikání spojené s operacemi komplexní Malování se odstraní.  
  
## <a name="default-double-buffering"></a>Výchozí dvojité ukládání do vyrovnávací paměti  
 Nejjednodušší způsob, jak pomocí dvojité vyrovnávací paměti v aplikacích se má použít výchozí dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky, které je součástí rozhraní .NET Framework. Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti pro formuláře Windows a vytvořené ovládacích prvků Windows tak, že nastavíte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true` nebo s použitím <xref:System.Windows.Forms.Control.SetStyle%2A> metoda. Další informace najdete v tématu [jak: Omezení blikání grafiky dvojité ukládání do vyrovnávací paměti pro formuláře a ovládací prvky](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Ruční správa grafiky uložené do vyrovnávací paměti  
 Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo rozšířené paměti pro správu vám pomůže tříd rozhraní .NET Framework implementovat vlastní logiku na dvojité ukládání do vyrovnávací paměti. Je třída, která je zodpovědná za přidělení a správa jednotlivých grafické vyrovnávací paměti <xref:System.Drawing.BufferedGraphicsContext> třídy. Každá doména aplikace má vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> instance, která spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro příslušnou aplikaci. Ve většině případů bude pouze jednu doménu aplikace na aplikaci, takže obvykle není jeden výchozí <xref:System.Drawing.BufferedGraphicsContext> na aplikaci. Výchozí <xref:System.Drawing.BufferedGraphicsContext> instancí jsou spravována <xref:System.Drawing.BufferedGraphicsManager> třídy. Můžete načíst odkaz na výchozí hodnotu <xref:System.Drawing.BufferedGraphicsContext> instance voláním <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Můžete také vytvořit vyhrazený <xref:System.Drawing.BufferedGraphicsContext> instance, což může zlepšit výkon pro graficky náročné aplikace. Informace o tom, jak vytvořit <xref:System.Drawing.BufferedGraphicsContext> instance najdete v tématu [jak: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Ruční zobrazení grafiky uložené do vyrovnávací paměti  
 Můžete použít instanci <xref:System.Drawing.BufferedGraphicsContext> třídy za účelem vytvoření grafické vyrovnávací paměti při volání <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, která vrací instanci <xref:System.Drawing.BufferedGraphics> třídy. A <xref:System.Drawing.BufferedGraphics> objektu spravuje vyrovnávací paměť, která souvisí s vykreslovací plochu, jako je například formulář nebo ovládací prvek.  
  
 Jakmile je vytvořena instance, <xref:System.Drawing.BufferedGraphics> třída spravuje vykreslování pro vyrovnávací paměť grafiky v paměti. Můžete vygenerovat grafické vyrovnávací paměti prostřednictvím <xref:System.Drawing.BufferedGraphics.Graphics%2A>, která zveřejňuje <xref:System.Drawing.Graphics> objekt reprezentující přímo vyrovnávací paměti. Můžete vykreslení tohoto <xref:System.Drawing.Graphics> objektu stejně, jako byste to udělali <xref:System.Drawing.Graphics> objekt, který reprezentuje návrhovém povrchu. Po vykreslení na obrázcích do vyrovnávací paměti můžete použít <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> chcete zkopírovat obsah vyrovnávací paměti na návrhovém povrchu na obrazovce.  
  
 Další informace o používání <xref:System.Drawing.BufferedGraphics> najdete v tématu [ručně vykreslování ukládány do vyrovnávací paměti grafiky](how-to-manually-render-buffered-graphics.md). Další informace o vykreslování grafiky, naleznete v tématu [grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.BufferedGraphics>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphicsManager>
- [Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti](how-to-manually-render-buffered-graphics.md)
- [Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)
- [Postupy: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md)
- [Grafika a kreslení v rozhraní Windows Forms](graphics-and-drawing-in-windows-forms.md)
