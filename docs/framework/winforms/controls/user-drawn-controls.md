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
ms.openlocfilehash: e9eab78695db128c0538914c5364aaa54c135403
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509958"
---
# <a name="user-drawn-controls"></a>Ovládací prvky vykreslované uživatelem
Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky. Můžete vytvořit uživatelský ovládací prvek je sada standardních ovládacích prvků kódu jsou technologicky propojené, nebo si můžete navrhnout vlastní ovládací prvek od základů. Dědičnost můžete použít i k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidejte do jeho vlastní funkce. Jakýkoli přístup, můžete použít, rozhraní .NET Framework poskytuje funkce pro kreslení vlastní grafické rozhraní pro libovolný ovládací prvek, který vytvoříte.  
  
 Vykreslování ovládacího prvku lze dosáhnout spuštění kódu v ovládacím prvku <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda <xref:System.Windows.Forms.PaintEventArgs> objektu, který obsahuje všechny informace a funkce pro vykreslení ovládacího prvku. <xref:System.Windows.Forms.PaintEventArgs> Jako vlastnosti poskytuje dva hlavní objekty, které se použije při vykreslování ovládacího prvku:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt - obdélník, který představuje část ovládacího prvku, který bude vykreslen. To může být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak vykreslit ovládací prvek.  
  
-   <xref:System.Drawing.Graphics> objekt - zapouzdřuje několik orientované grafické objekty a metody, které poskytují funkce, které jsou potřebné k vykreslení ovládacího prvku.  
  
 Další informace o <xref:System.Drawing.Graphics> objekt a jak ho použít, najdete v článku [jak: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Událost se aktivuje vždy, když je ovládací prvek vykreslen nebo aktualizovat na obrazovce a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt představuje obdélník, ve kterém se Malování proběhnout. Pokud je potřeba aktualizovat, celý ovládací prvek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude představovat velikost celý ovládací prvek. Pokud pouze část ovládacího prvku musí aktualizovat, ale <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objektů bude představovat jenom oblasti, kterou je potřeba se měl překreslit. Příklad takovém případě se při ovládacího prvku byla částečně zakrytý jiného ovládacího prvku nebo formuláře v uživatelském rozhraní.  
  
 Při dědění z <xref:System.Windows.Forms.Control> třídy, je nutné přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu a zadejte kód pro vykreslování grafiky v rámci. Pokud chcete poskytnout vlastní grafické rozhraní pro uživatelský ovládací prvek nebo zděděný ovládací prvek, lze také uděláte tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Příklad je uveden níže:  
  
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
  
 Předchozí příklad ukazuje, jak k vykreslení ovládacího prvku pomocí velmi jednoduchá grafická reprezentace. Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy, vytvoří <xref:System.Drawing.Pen> objektu, pomocí kterého se má kreslit a nakonec kreslení na tři tečky v obdélníku určené <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku. I když většina vykreslování kód bude složitější než toto, tento příklad ukazuje použití <xref:System.Drawing.Graphics> obsažené v objektu <xref:System.Windows.Forms.PaintEventArgs> objektu. Všimněte si, že pokud se dědí z třídy, která už má grafickou reprezentaci, například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>a nechcete, aby začlenit tohoto vyjádření do vaší vykreslování, neměli by jste volat základní třídy <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.  
  
 Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metoda ovládacího prvku se spustí při prvním vykreslení ovládacího prvku a pokaždé, když se aktualizuje. Aby bylo zajištěno, že pokaždé, když je velikost překreslení ovládacího prvku, přidejte následující řádek do konstruktoru ovládacího prvku:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Použití <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnost pro implementaci neobdélníkových ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
- [Základní ovládací prvky](../../../../docs/framework/winforms/controls/constituent-controls.md)
- [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
