---
title: Vykreslení ovládacího prvku Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="rendering-a-windows-forms-control"></a>Vykreslení ovládacího prvku Windows Forms
Vykreslování odkazuje na proces vytváření vizuální reprezentace na obrazovce uživatele. Windows Forms používá [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (nové Windows grafiky knihovny) pro vykreslování. Spravované třídy, které poskytují přístup k [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] v <xref:System.Drawing?displayProperty=nameWithType> obor názvů a jeho podobory.  
  
 Tyto prvky jsou součástí vykreslování ovládacího prvku:  
  
-   Kreslení funkce poskytované službou základní třídy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
-   Základní prvky [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] grafiky knihovny.  
  
-   Geometrie kreslení oblast.  
  
-   Postup uvolnění grafické prostředky.  
  
## <a name="drawing-functionality-provided-by-control"></a>Kreslení funkce poskytované službou ovládací prvek  
 Základní třída <xref:System.Windows.Forms.Control> poskytuje kreslení funkce prostřednictvím jeho <xref:System.Windows.Forms.Control.Paint> událostí. Ovládací prvek vyvolá <xref:System.Windows.Forms.Control.Paint> událost vždy, když je nutné aktualizovat jeho zobrazení. Další informace o událostech v rozhraní .NET Framework, najdete v části [zpracování a vyvolávání událostí](../../../../docs/standard/events/index.md).  
  
 Data události jsou třídy pro <xref:System.Windows.Forms.Control.Paint> událostí, <xref:System.Windows.Forms.PaintEventArgs>, obsahuje data potřebná pro vykreslení ovládacího prvku – popisovač pro objekt grafiky a obdélníku objekt, který reprezentuje k vykreslení oblasti. Tyto objekty se zobrazují v nabízeném následující fragment kódu.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> je spravovaný třída, která zapouzdřuje kreslení funkce, jak je popsáno v diskusi o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dál v tomto tématu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Je instance <xref:System.Drawing.Rectangle> struktury a definuje dostupné oblasti, ve kterém můžete vykreslení ovládacího prvku. Můžete vypočítat vývojář ovládacího prvku <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> pomocí <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastností ovládacího prvku, jak je popsáno v diskusi o geometrie později v tomto tématu.  
  
 Ovládací prvek musí poskytnout vykreslování logiku přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metoda, která dědí z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> získá přístup k objektu grafiky a prostřednictvím kreslení obdélníku <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnosti <xref:System.Windows.Forms.PaintEventArgs> do ní předán instance.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda základu <xref:System.Windows.Forms.Control> třída neimplementuje žádné kreslení funkce, ale jenom vyvolá delegáti událostí, které jsou registrovány <xref:System.Windows.Forms.Control.Paint> událostí. Při přepsání <xref:System.Windows.Forms.Control.OnPaint%2A>, obvykle by měla vyvolat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy, které registrováno delegáti přijímat <xref:System.Windows.Forms.Control.Paint> událostí. Ovládací prvky, které malovat jejich celý prostor by neměl však vyvolání základní třídy <xref:System.Windows.Forms.Control.OnPaint%2A>, jak vzniká blikání. Příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> událostí, najdete v článku [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Nevolejte <xref:System.Windows.Forms.Control.OnPaint%2A> přímo z ovládacího prvku; místo toho vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (zděděno z <xref:System.Windows.Forms.Control>) nebo jiné metody, která volá <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Zase vyvolá metoda <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Metoda je přetížena a v závislosti na argumenty zadané <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, některé nebo všechny jeho oblasti obrazovky ho překreslí ovládacího prvku.  
  
 Základní <xref:System.Windows.Forms.Control> třída definuje jinou metodu, které jsou užitečné pro kreslení – <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metoda.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> vybarví na pozadí (a tím tvaru) okna a záruku, že se rychlá při <xref:System.Windows.Forms.Control.OnPaint%2A> vybarví podrobnosti a může být pomalejší, protože požadavky jednotlivých Malování jsou sloučeny do jednoho <xref:System.Windows.Forms.Control.Paint> událostí, které pokrývá všechny oblasti, které mají být překreslen. Můžete chtít vyvolání <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Pokud například chcete kreslení přechodu stejné barvy pozadí pro vlastní ovládací prvek.  
  
 Při <xref:System.Windows.Forms.Control.OnPaintBackground%2A> má klasifikace podobných událostí a trvá stejný argument jako `OnPaint` metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> není metoda true událostí. Neexistuje žádné `PaintBackground` událostí a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nevyvolá – delegáti událostí. Při přepsání <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody odvozené třídě není nutné volat <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metoda její základní třída.  
  
## <a name="gdi-basics"></a>Základní informace o GDI +  
 <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení různé tvary, například kružnice, trojúhelníčky, oblouky a výpustky, jakož i metody pro zobrazení textu. <xref:System.Drawing?displayProperty=nameWithType> Obor názvů a jeho podobory obsahují třídy, které zapouzdřují grafické prvky, jako jsou například tvarů (kroužky, obdélníky, oblouky a dalších), barvy, písma, štětce a tak dále. Další informace o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], najdete v části [použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md). Se základy [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] jsou také popsány v [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometrie oblasti kreslení  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Vlastnost ovládacího prvku určuje obdélníkovou oblast, která je k dispozici do ovládacího prvku na obrazovce uživatele, když <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs> určuje k oblasti, která je ve skutečnosti vykresluje. (Nezapomeňte, že Malování se provádí v <xref:System.Windows.Forms.Control.Paint> metody událostí, která přijímá <xref:System.Windows.Forms.PaintEventArgs> instance jako její argument). Ovládací prvek se může být potřeba malovat pouze část jeho dostupné oblasti, stejně jako v případě, když malý změn zobrazení ovládacího prvku. V těchto situacích, musí vývojář řízení výpočetní skutečné obdélníku pro kreslení a aby předat <xref:System.Windows.Forms.Control.Invalidate%2A>. Přetížené verze <xref:System.Windows.Forms.Control.Invalidate%2A> trvají <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.Region> jako argument ke generování použijte tento argument <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Následující kód fragmentovat ukazuje jak `FlashTrackBar` vlastního ovládacího prvku vypočítá obdélníkovou oblast k vykreslení. `client` Proměnné označuje <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost. Kompletní příklad, najdete v části [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Uvolnění grafické prostředky  
 Grafické objekty jsou náročná, protože používají systémové prostředky. Tyto objekty zahrnují instance <xref:System.Drawing.Graphics?displayProperty=nameWithType> třídy a instance <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>a dalších grafických tříd. Je důležité vytvořit prostředek grafiky jenom v případě, že ho potřebovat a vydání ho brzy budete hotovi, jeho použití. Pokud vytvoříte typ, který implementuje <xref:System.IDisposable> rozhraní, volejte jeho <xref:System.IDisposable.Dispose%2A> metoda až skončíte s ním k uvolnění prostředků.  
  
 Následující kód fragmentovat ukazuje jak `FlashTrackBar` vlastního ovládacího prvku vytvoří a uvolní <xref:System.Drawing.Brush> prostředků. Úplný zdrojový kód, najdete v části [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
