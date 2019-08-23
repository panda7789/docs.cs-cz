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
ms.openlocfilehash: b24fbefac0dcfb666e25ad1d1726ef2cf8a5d84e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968278"
---
# <a name="rendering-a-windows-forms-control"></a>Vykreslení ovládacího prvku Windows Forms
Vykreslování odkazuje na proces vytvoření vizuální reprezentace na obrazovce uživatele. Model Windows Forms pro vykreslování používá GDI (novou knihovnu Windows Graphics Library). Spravované třídy, které poskytují přístup k rozhraní GDI, jsou <xref:System.Drawing?displayProperty=nameWithType> v oboru názvů a v jeho podřízených oborech názvů.  
  
 Následující prvky jsou zapojeny do vykreslování ovládacích prvků:  
  
- Funkce kreslení poskytovaná základní třídou <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Základní prvky knihovny grafiky GDI.  
  
- Geometrie oblasti kreslení  
  
- Postup pro uvolnění grafických prostředků  
  
## <a name="drawing-functionality-provided-by-control"></a>Funkce kreslení poskytované ovládacím prvkem  
 Základní třída <xref:System.Windows.Forms.Control> poskytuje funkce kreslení prostřednictvím své <xref:System.Windows.Forms.Control.Paint> události. Ovládací prvek vyvolá <xref:System.Windows.Forms.Control.Paint> událost vždy, když je potřeba aktualizovat svůj displej. Další informace o událostech v .NET Framework naleznete v tématu [manipulace a vyvolávání událostí](../../../standard/events/index.md).  
  
 Třída dat události pro <xref:System.Windows.Forms.Control.Paint> <xref:System.Windows.Forms.PaintEventArgs>událost, obsahuje data potřebná pro vykreslení ovládacího prvku – popisovač objektu grafiky a obdélníkový objekt, který představuje oblast pro vykreslení. Tyto objekty jsou v následujícím fragmentu kódu zobrazeny tučně.  
  
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
  
 <xref:System.Drawing.Graphics>je spravovaná třída, která zapouzdřuje funkce kreslení, jak je popsáno v diskuzi o GDI dále v tomto tématu. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Je instancí<xref:System.Drawing.Rectangle> struktury a definuje oblast k dispozici, ve které může ovládací prvek vykreslovat. Vývojář ovládacího prvku může vypočítat <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> pomocí vlastnosti ovládacího prvku, jak je popsáno v diskuzi o geometrii dále v tomto tématu.  
  
 Ovládací prvek musí poskytovat logiku vykreslování přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody, ze <xref:System.Windows.Forms.Control>které dědí. <xref:System.Windows.Forms.Control.OnPaint%2A>Získá přístup k objektu grafiky a obdélník, který se nakreslí přes <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> a vlastnosti <xref:System.Windows.Forms.PaintEventArgs> instance, která je předána.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Metoda základní <xref:System.Windows.Forms.Control> třídy neimplementuje žádné funkce kreslení <xref:System.Windows.Forms.Control.Paint> , ale vyvolá pouze delegáty událostí, které jsou zaregistrovány s událostí. <xref:System.Windows.Forms.Control.OnPaint%2A> Při přepsání <xref:System.Windows.Forms.Control.OnPaint%2A>byste měli obvykle <xref:System.Windows.Forms.Control.OnPaint%2A> vyvolat metodu základní třídy <xref:System.Windows.Forms.Control.Paint> , aby registrovaní delegáti obdrželi událost. Nicméně ovládací prvky, které vykreslí celý povrch <xref:System.Windows.Forms.Control.OnPaint%2A>, by neměly vyvolat základní třídu, protože to představuje blikání. Příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> události [naleznete v tématu How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.  
  
> [!NOTE]
> Nevolejte <xref:System.Windows.Forms.Control.OnPaint%2A> přímo z vašeho ovládacího prvku. místo toho <xref:System.Windows.Forms.Control.Invalidate%2A> volejte metodu (zděděnou od <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Control.Invalidate%2A>) nebo jinou metodu, která vyvolá. <xref:System.Windows.Forms.Control.Invalidate%2A> Metoda zase vyvolá metodu <xref:System.Windows.Forms.Control.OnPaint%2A>. Metoda je přetížena a v závislosti na argumentech dodaných do <xref:System.Windows.Forms.Control.Invalidate%2A> `e`ovládací prvek překreslí buď jednu nebo celou jeho oblast obrazovky. <xref:System.Windows.Forms.Control.Invalidate%2A>  
  
 Základní <xref:System.Windows.Forms.Control> třída definuje další metodu, která je užitečná pro kreslení <xref:System.Windows.Forms.Control.OnPaintBackground%2A> – metoda.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>vykreslí pozadí (a tím i tvar) okna a zaručuje, že bude rychlá, zatímco <xref:System.Windows.Forms.Control.OnPaint%2A> jednotlivé požadavky na malování jsou zkombinovány do jedné <xref:System.Windows.Forms.Control.Paint> události, která se vztahuje na všechny oblasti, které musí být překreslit. Může být vhodné vyvolat <xref:System.Windows.Forms.Control.OnPaintBackground%2A> if, například, chcete-li nakreslit barevné pozadí pro ovládací prvek.  
  
 I <xref:System.Windows.Forms.Control.OnPaintBackground%2A> když má klasifikaci typu událost a přebírá stejný argument `OnPaint` jako metoda, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> není metodou skutečné události. Neexistuje žádná `PaintBackground` událost a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nevyvolává delegáty událostí. Při přepsání <xref:System.Windows.Forms.Control.OnPaintBackground%2A> metody není k <xref:System.Windows.Forms.Control.OnPaintBackground%2A> vyvolání metody základní třídy nutné použít odvozenou třídu.  
  
## <a name="gdi-basics"></a>Základy GDI+  
 <xref:System.Drawing.Graphics> Třída poskytuje metody pro kreslení různých tvarů, jako jsou kruhy, trojúhelníky, elipsy a elipsy, a také metody pro zobrazení textu. <xref:System.Drawing?displayProperty=nameWithType> Obor názvů a jeho podobory názvů obsahují třídy, které zapouzdřují grafické prvky, jako jsou tvary (kružnice, obdélníky, elipsy a další), barvy, písma, štětce atd. Další informace o rozhraní GDI najdete v tématu [použití spravovaných grafických tříd](../advanced/using-managed-graphics-classes.md). Základy GDI jsou také popsány v [tématu How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.  
  
## <a name="geometry-of-the-drawing-region"></a>Geometrie oblasti kreslení  
 Vlastnost ovládacího prvku určuje obdélníkovou oblast dostupnou ovládacímu prvku na obrazovce uživatele, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> zatímco vlastnost <xref:System.Windows.Forms.PaintEventArgs> určuje oblast, která je ve skutečnosti vykreslena. <xref:System.Windows.Forms.Control.ClientRectangle%2A> (Nezapomeňte, že Malování je provedeno v <xref:System.Windows.Forms.Control.Paint> metodě Event, která jako <xref:System.Windows.Forms.PaintEventArgs> Argument přijímá instanci). Ovládací prvek může být nutné malovat pouze část dostupné oblasti, jak je v případě, že se změní malá část zobrazení ovládacího prvku. V těchto situacích musí vývojář ovládacího prvku vypočítat skutečný obdélník, který se má vykreslit a předat do <xref:System.Windows.Forms.Control.Invalidate%2A>. Přetížené <xref:System.Windows.Forms.Control.Invalidate%2A> verze, které <xref:System.Drawing.Region> <xref:System.Drawing.Rectangle> přebírají nebo jako argument <xref:System.Windows.Forms.PaintEventArgs>používají tento argument pro vygenerování <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnosti.  
  
 Následující fragment kódu ukazuje, jak `FlashTrackBar` vlastní ovládací prvek vypočítá obdélníkovou oblast pro vykreslení. `client` Proměnná označuje<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnost. Úplnou ukázku najdete v tématu [How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Uvolnění grafických prostředků  
 Grafické objekty jsou nákladné, protože využívají systémové prostředky. Takové objekty zahrnují instance <xref:System.Drawing.Graphics?displayProperty=nameWithType> třídy a také <xref:System.Drawing.Brush?displayProperty=nameWithType>instance, <xref:System.Drawing.Pen?displayProperty=nameWithType>a další grafické třídy. Je důležité, abyste vytvořili prostředek grafiky, jenom když ho potřebujete, a vydáte ho hned po jeho použití. Pokud vytvoříte typ, který implementuje <xref:System.IDisposable> rozhraní, zavolejte jeho <xref:System.IDisposable.Dispose%2A> metodu, jakmile se dokončíte, aby se uvolnily prostředky.  
  
 Následující fragment kódu ukazuje, jak `FlashTrackBar` vlastní ovládací prvek vytvoří a <xref:System.Drawing.Brush> uvolní prostředek. Úplný zdrojový kód naleznete v tématu [How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření ovládacího prvku model Windows Forms, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md)
