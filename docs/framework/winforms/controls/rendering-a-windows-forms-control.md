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
ms.openlocfilehash: 9641b6906bc2acaa525aed6df57f189d39317d35
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614666"
---
# <a name="rendering-a-windows-forms-control"></a>Vykreslení ovládacího prvku Windows Forms
Vykreslování se vztahuje k procesu vytváření vizuální reprezentace na obrazovce uživatele. Windows Forms používá [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (nové Windows grafické knihovny) pro vykreslování. Spravované třídy, které poskytují přístup k [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] v <xref:System.Drawing?displayProperty=nameWithType> obor názvů a jeho podobory.  
  
 Tyto prvky jsou součástí vykreslování ovládacího prvku:  
  
- Kreslení funkce poskytované službou základní třídy <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Základní prvky [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] grafické knihovny.  
  
- Geometrie oblasti výkresu.  
  
- Postup uvolnění grafické prostředky.  
  
## <a name="drawing-functionality-provided-by-control"></a>Kreslení funkce poskytované službou ovládacího prvku  
 Základní třída <xref:System.Windows.Forms.Control> poskytuje výkresu funkce prostřednictvím jeho <xref:System.Windows.Forms.Control.Paint> událostí. Ovládací prvek vyvolá <xref:System.Windows.Forms.Control.Paint> událost, kdykoliv je nutné aktualizovat zobrazení. Další informace o události v rozhraní .NET Framework najdete v tématu [Handling and Raising Events](../../../standard/events/index.md).  
  
 Třída dat události pro <xref:System.Windows.Forms.Control.Paint> události, <xref:System.Windows.Forms.PaintEventArgs>, obsahuje data potřebná pro kreslení ovládacího prvku – popisovač pro grafický objekt a objekt obdélník, který představuje oblasti pro kreslení. Tyto objekty jsou uvedeny v tučně v následující fragment kódu.  
  
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
  
 <xref:System.Drawing.Graphics> je spravovanou třídu, která zapouzdřuje funkce kreslení, jak je popsáno v diskuzi o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dále v tomto tématu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Je instance <xref:System.Drawing.Rectangle> struktury a definuje dostupné oblasti, ve kterém můžete ovládací prvek nakreslit. Můžete vypočítat vývojářem ovládacího prvku <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> pomocí <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost ovládacího prvku, jak je popsáno v diskuzi o geometrii dále v tomto tématu.  
  
 Ovládací prvek musí poskytnout logiku vykreslování tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metodu, která dědí z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> získá přístup k grafický objekt a obdélník a kreslete prostřednictvím <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnosti <xref:System.Windows.Forms.PaintEventArgs> do něho předaný instance.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Metody základní třídy <xref:System.Windows.Forms.Control> třída neimplementuje žádné výkresu funkce, ale pouze vyvolá událost delegáty, které jsou registrované <xref:System.Windows.Forms.Control.Paint> událostí. Při přepsání <xref:System.Windows.Forms.Control.OnPaint%2A>, obvykle by měla vyvolat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy tak, která delegátů zaregistrovaný, zobrazí <xref:System.Windows.Forms.Control.Paint> událostí. Však ovládací prvky, které vykreslení jejich celého povrchu by neměl volat základní třídy <xref:System.Windows.Forms.Control.OnPaint%2A>, protože zavádí blikání. Příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> událostí, najdete v článku [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
>  Nelze vyvolat <xref:System.Windows.Forms.Control.OnPaint%2A> přímo z ovládacího prvku; místo toho vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> – metoda (zděděno z <xref:System.Windows.Forms.Control>) nebo jiné metody, která volá <xref:System.Windows.Forms.Control.Invalidate%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Následně vyvolá metodu <xref:System.Windows.Forms.Control.OnPaint%2A>. <xref:System.Windows.Forms.Control.Invalidate%2A> Přetížené metody, a v závislosti na argumenty předány <xref:System.Windows.Forms.Control.Invalidate%2A> `e`, ovládací prvek překreslí některé nebo všechny jeho oblast obrazovky.  
  
 Základní <xref:System.Windows.Forms.Control> třída definuje další metody, které jsou užitečné pro kreslení – <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> jsou vykreslovány na pozadí (a tím současně tvar) okna, je zaručeno, že bude rychlé, při <xref:System.Windows.Forms.Control.OnPaint%2A> jsou vykreslovány podrobnosti a může být pomalejší, protože jednotlivé malířského požadavky jsou zkombinované do jedné <xref:System.Windows.Forms.Control.Paint> událost, která se vztahuje na všechny oblasti, které mají být překreslení. Můžete chtít volat <xref:System.Windows.Forms.Control.OnPaintBackground%2A> Pokud například chcete kreslit barevné přechodu pozadí ovládacího prvku.  
  
 Zatímco <xref:System.Windows.Forms.Control.OnPaintBackground%2A> má nomenklaturu podobných událostí a používá stejný argument jako `OnPaint` metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> není metoda true události. Neexistuje žádná `PaintBackground` událostí a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nevyvolá – delegáti událostí. Při přepsání <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody odvozené třídy není potřeba vyvolat <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metodu své základní třídy.  
  
## <a name="gdi-basics"></a>Základní informace o rozhraní GDI +  
 <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení různých tvarů, například kružnice, trojúhelníků, oblouky a symbol tří teček, jakož i metody pro zobrazení textu. <xref:System.Drawing?displayProperty=nameWithType> Obor názvů a jeho podobory obsahují třídy, které zapouzdřují grafické prvky, jako jsou například obrazce (kruzích, obdélníky, oblouky a dalších), barvy, písma, štětců a tak dále. Další informace o [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], naleznete v tématu [použití spravovaných grafických tříd](../advanced/using-managed-graphics-classes.md). Se základy [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] jsou také popsány v [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometrie oblasti výkresu  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A> Vlastnost ovládacího prvku určuje obdélníkovou oblast k dispozici pro ovládací prvek na obrazovce uživatele, zatímco <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs> určuje oblast, která je ve skutečnosti překreslit. (Mějte na paměti, že Malování se provádí v <xref:System.Windows.Forms.Control.Paint> metoda události, která přijímá <xref:System.Windows.Forms.PaintEventArgs> instanci jako argument). Ovládací prvek může být nutné vykreslení pouze část jeho dostupné oblasti, stejně jako v případě, pokud malá část ovládacího prvku zobrazení změn. V takových situacích, musí vývojář ovládacího prvku compute skutečné obdélník kreslete a předat ho do <xref:System.Windows.Forms.Control.Invalidate%2A>. Přetížené verze <xref:System.Windows.Forms.Control.Invalidate%2A> trvají <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.Region> jako argument používat ke generování tento argument <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Následující kód fragmentu ukazuje jak `FlashTrackBar` vlastního ovládacího prvku vypočítá obdélníkovou oblast, chcete-li nakreslit. `client` Označuje proměnnou <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost. Úplnou ukázku najdete v tématu [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Uvolnění grafické prostředky  
 Grafické objekty jsou nákladná, protože používají systémové prostředky. Tyto objekty patří instance <xref:System.Drawing.Graphics?displayProperty=nameWithType> třídy a instance <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>a jiných grafických tříd. Je důležité vytvořit prostředek grafiky pouze v případě potřeby a ji brzy budete mít, jeho použití. Pokud vytvoříte typ, který implementuje <xref:System.IDisposable> rozhraní, zavolejte jeho <xref:System.IDisposable.Dispose%2A> metoda až skončíte s ním k uvolnění prostředků.  
  
 Kód následující fragment ukazuje jak `FlashTrackBar` vytvoří vlastní ovládací prvek a uvolní <xref:System.Drawing.Brush> prostředků. Úplný zdrojový kód, naleznete v tématu [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md)
