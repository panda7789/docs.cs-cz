---
title: Ovládací prvky vykreslované uživatelem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182013"
---
# <a name="user-drawn-controls"></a>Ovládací prvky vykreslované uživatelem
Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky. Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků vázaných kódem, nebo můžete navrhnout vlastní ovládací prvek od základů. Dědičnost můžete dokonce použít k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidat k jeho vlastní funkce. Bez ohledu na přístup, který použijete, rozhraní .NET Framework poskytuje funkce pro nakreslení vlastního grafického rozhraní pro libovolný ovládací prvek, který vytvoříte.  
  
 Malování ovládacího prvku se provádí spuštěním kódu v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku. Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody je <xref:System.Windows.Forms.PaintEventArgs> objekt, který poskytuje všechny informace a funkce potřebné k vykreslení ovládacího prvku. Poskytuje <xref:System.Windows.Forms.PaintEventArgs> jako vlastnosti dva hlavní objekty, které budou použity při vykreslování ovládacího prvku:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objekt - obdélník, který představuje část ovládacího prvku, který bude nakreslena. To může být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak je nakreslena ovládacího prvku.  
  
- <xref:System.Drawing.Graphics>object - zapouzdřuje několik objektů a metod orientovaných na grafiku, které poskytují funkce potřebné k nakreslení ovládacího prvku.  
  
 Další informace o <xref:System.Drawing.Graphics> objektu a jeho použití naleznete v [tématu How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 Událost <xref:System.Windows.Forms.Control.OnPaint%2A> je aktivována vždy, když je ovládací prvek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nakreslena nebo aktualizována na obrazovce a objekt představuje obdélník, ve kterém bude malování probíhat. Pokud je třeba aktualizovat celý ovládací <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> prvek, bude představovat velikost celého ovládacího prvku. Pokud je však třeba aktualizovat pouze část <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ovládacího prvku, bude objekt představovat pouze oblast, kterou je třeba překreslit. Příkladem takového případu by bylo, když byl ovládací prvek částečně zakryt jiným ovládacím prvkem nebo formulářem v uživatelském rozhraní.  
  
 Při dědění <xref:System.Windows.Forms.Control> z třídy, <xref:System.Windows.Forms.Control.OnPaint%2A> je nutné přepsat metodu a poskytnout kód vykreslování grafiky uvnitř. Pokud chcete poskytnout vlastní grafické rozhraní uživatelského ovládacího prvku nebo zděděného ovládacího prvku, můžete tak učinit také přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Příklad najdete níže:  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 Předchozí příklad ukazuje, jak vykreslit ovládací prvek s velmi jednoduchou grafickou reprezentací. Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu základní třídy, vytvoří <xref:System.Drawing.Pen> objekt, se kterým chcete kreslit, a nakonec nakreslí <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> elipsu v obdélníku určeném ovládacím prvkem a. Ačkoli většina vykreslovací kód bude výrazně složitější <xref:System.Drawing.Graphics> než tento, <xref:System.Windows.Forms.PaintEventArgs> tento příklad ukazuje použití objektu obsaženého v objektu. Všimněte si, že pokud dědíte z třídy, <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>která již má grafické znázornění, například nebo , a nechcete <xref:System.Windows.Forms.Control.OnPaint%2A> začlenit tuto reprezentaci do vykreslování, neměli byste volat metodu základní třídy.  
  
 Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku se spustí při prvním vykreslení ovládacího prvku a při každém aktualizaci. Chcete-li zajistit, že váš ovládací prvek je překreslen při každém jeho velikosti, přidejte následující řádek k konstruktoru ovládacího prvku:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Pomocí <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnosti implementujte neobdélníkový ovládací prvek.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Postupy: Vytváření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Základní ovládací prvky](constituent-controls.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
