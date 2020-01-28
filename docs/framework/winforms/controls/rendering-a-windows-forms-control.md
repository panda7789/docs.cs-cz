---
title: Vykreslení ovládacího prvku
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
ms.openlocfilehash: 0e1a7ca5dc0414d518c081b1db2dca5477d4f743
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742383"
---
# <a name="rendering-a-windows-forms-control"></a>Vykreslení ovládacího prvku Windows Forms
Vykreslování odkazuje na proces vytvoření vizuální reprezentace na obrazovce uživatele. Model Windows Forms pro vykreslování používá GDI (novou knihovnu Windows Graphics Library). Spravované třídy, které poskytují přístup k rozhraní GDI, jsou v oboru názvů <xref:System.Drawing?displayProperty=nameWithType> a jeho podobory názvů.  
  
 Následující prvky jsou zapojeny do vykreslování ovládacích prvků:  
  
- Funkce kreslení poskytnutá základní třídou <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
- Základní prvky knihovny grafiky GDI.  
  
- Geometrie oblasti kreslení  
  
- Postup pro uvolnění grafických prostředků  
  
## <a name="drawing-functionality-provided-by-control"></a>Funkce kreslení poskytované ovládacím prvkem  
 Základní třída <xref:System.Windows.Forms.Control> poskytuje funkce kreslení prostřednictvím události <xref:System.Windows.Forms.Control.Paint>. Ovládací prvek vyvolá událost <xref:System.Windows.Forms.Control.Paint> vždy, když je potřeba aktualizovat svůj displej. Další informace o událostech v .NET Framework naleznete v tématu [manipulace a vyvolávání událostí](../../../standard/events/index.md).  
  
 Třída dat události pro událost <xref:System.Windows.Forms.Control.Paint>, <xref:System.Windows.Forms.PaintEventArgs>, obsahuje data potřebná pro vykreslení ovládacího prvku – popisovač objektu grafiky a obdélníkový objekt, který představuje oblast pro vykreslení. Tyto objekty jsou v následujícím fragmentu kódu zobrazeny tučně.  
  
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
  
 <xref:System.Drawing.Graphics> je spravovaná třída, která zapouzdřuje funkce kreslení, jak je popsáno dále v tomto tématu v diskuzi o GDI. <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> je instance <xref:System.Drawing.Rectangle> struktury a definuje dostupnou oblast, ve které může ovládací prvek vykreslovat. Vývojář ovládacího prvku může vypočítat <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> pomocí vlastnosti <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ovládacího prvku, jak je popsáno v diskuzi o geometrii dále v tomto tématu.  
  
 Ovládací prvek musí poskytovat logiku vykreslování přepsáním metody <xref:System.Windows.Forms.Control.OnPaint%2A>, kterou dědí z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.Control.OnPaint%2A> získá přístup k objektu grafiky a obdélník, který se nakreslí přes <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> vlastnosti předané instance <xref:System.Windows.Forms.PaintEventArgs>.  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> základní <xref:System.Windows.Forms.Control> třídy neimplementuje žádné funkce kreslení, ale pouze vyvolá delegáty událostí, které jsou zaregistrovány v události <xref:System.Windows.Forms.Control.Paint>. Pokud přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A>, měli byste obvykle vyvolat metodu <xref:System.Windows.Forms.Control.OnPaint%2A> základní třídy, aby registrovaní delegáti obdrželi událost <xref:System.Windows.Forms.Control.Paint>. Nicméně ovládací prvky, které malují celou plochu, by neměly vyvolat <xref:System.Windows.Forms.Control.OnPaint%2A>základní třídy, protože to představuje blikání. Příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> události naleznete v tématu [How to: Create a model Windows Forms Control, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
> [!NOTE]
> Nevolejte <xref:System.Windows.Forms.Control.OnPaint%2A> přímo z vašeho ovládacího prvku; místo toho volejte metodu <xref:System.Windows.Forms.Control.Invalidate%2A> (zděděná z <xref:System.Windows.Forms.Control>) nebo jinou metodu, která vyvolá <xref:System.Windows.Forms.Control.Invalidate%2A>. Metoda <xref:System.Windows.Forms.Control.Invalidate%2A> zase vyvolá <xref:System.Windows.Forms.Control.OnPaint%2A>. Metoda <xref:System.Windows.Forms.Control.Invalidate%2A> je přetížena a v závislosti na argumentech dodaných <xref:System.Windows.Forms.Control.Invalidate%2A> `e`ovládací prvek překreslí buď jednu nebo celou jeho oblast obrazovky.  
  
 Základní třída <xref:System.Windows.Forms.Control> definuje další metodu, která je užitečná pro kreslení – metodou <xref:System.Windows.Forms.Control.OnPaintBackground%2A>.  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> vykreslí pozadí (a tím i tvar) okna a zaručuje, že bude rychlá, zatímco <xref:System.Windows.Forms.Control.OnPaint%2A> vykreslí podrobnosti a může být pomalejší, protože jednotlivé požadavky na malování jsou zkombinovány do jedné <xref:System.Windows.Forms.Control.Paint> události, která se vztahuje na všechny oblasti, které je nutné překreslit. Můžete chtít vyvolat <xref:System.Windows.Forms.Control.OnPaintBackground%2A>, pokud například chcete nakreslit barevné pozadí pro ovládací prvek.  
  
 I když <xref:System.Windows.Forms.Control.OnPaintBackground%2A> má klasifikaci podobné událostem a přebírá stejný argument jako metoda `OnPaint`, <xref:System.Windows.Forms.Control.OnPaintBackground%2A> není pravdivá metoda události. Neexistuje žádná `PaintBackground` událost a <xref:System.Windows.Forms.Control.OnPaintBackground%2A> nevyvolává delegáty událostí. Při přepsání metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> není k vyvolání metody <xref:System.Windows.Forms.Control.OnPaintBackground%2A> její základní třídy nutné použít odvozenou třídu.  
  
## <a name="gdi-basics"></a>Základy GDI+  
 Třída <xref:System.Drawing.Graphics> poskytuje metody pro kreslení různých tvarů, jako jsou kruhy, trojúhelníky, elipsy a elipsy, a také metody pro zobrazení textu. Obor názvů <xref:System.Drawing?displayProperty=nameWithType> a jeho podobory názvů obsahují třídy, které zapouzdřují grafické prvky, jako jsou například tvary (kružnice, obdélníky, elipsy a další), barvy, písma, štětce atd. Další informace o rozhraní GDI najdete v tématu [použití spravovaných grafických tříd](../advanced/using-managed-graphics-classes.md). Základy GDI jsou také popsány v tématu [Postupy: vytvoření model Windows Formsho ovládacího prvku, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="geometry-of-the-drawing-region"></a>Geometrie oblasti kreslení  
 Vlastnost <xref:System.Windows.Forms.Control.ClientRectangle%2A> ovládacího prvku určuje obdélníkovou oblast dostupnou ovládacímu prvku na obrazovce uživatele, zatímco vlastnost <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs> určuje oblast, která je skutečně vykreslena. (Nezapomeňte, že Malování je provedeno v metodě <xref:System.Windows.Forms.Control.Paint> události, která přebírá instanci <xref:System.Windows.Forms.PaintEventArgs> jako argument). Ovládací prvek může být nutné malovat pouze část dostupné oblasti, jak je v případě, že se změní malá část zobrazení ovládacího prvku. V těchto situacích musí vývojář ovládacího prvku vypočítat skutečný obdélník pro vykreslování a předat <xref:System.Windows.Forms.Control.Invalidate%2A>. Přetížené verze <xref:System.Windows.Forms.Control.Invalidate%2A>, které přebírají <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.Region> jako argument, používají tento argument pro vygenerování vlastnosti <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> <xref:System.Windows.Forms.PaintEventArgs>.  
  
 Následující fragment kódu ukazuje, jak `FlashTrackBar` vlastní ovládací prvek vypočítá obdélníkovou oblast, do které se má kreslit. Proměnná `client` označuje vlastnost <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>. Úplnou ukázku naleznete v tématu [How to: Create a model Windows Forms Control, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>Uvolnění grafických prostředků  
 Grafické objekty jsou nákladné, protože využívají systémové prostředky. Takové objekty zahrnují instance <xref:System.Drawing.Graphics?displayProperty=nameWithType> třídy a také instance <xref:System.Drawing.Brush?displayProperty=nameWithType>, <xref:System.Drawing.Pen?displayProperty=nameWithType>a další třídy grafiky. Je důležité, abyste vytvořili prostředek grafiky, jenom když ho potřebujete, a vydáte ho hned po jeho použití. Pokud vytvoříte typ, který implementuje rozhraní <xref:System.IDisposable>, zavolejte jeho metodu <xref:System.IDisposable.Dispose%2A>, jakmile se s ním dokončíte, aby se uvolnily prostředky.  
  
 Následující fragment kódu ukazuje, jak `FlashTrackBar` vlastní ovládací prvek vytvoří a uvolní prostředek <xref:System.Drawing.Brush>. Úplný zdrojový kód naleznete v tématu [How to: Create a model Windows Forms Control, který zobrazuje průběh](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](how-to-create-a-windows-forms-control-that-shows-progress.md)
