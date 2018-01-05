---
title: "Ovládací prvky vykreslované uživatelem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e486058850616c2304ce0032c35baa855fdf2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="user-drawn-controls"></a>Ovládací prvky vykreslované uživatelem
Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky. Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků spojuje kód, nebo můžete navrhnout vlastní ovládací prvek od základů nahoru. Dědičnost i slouží k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidejte do jeho vyplývajících funkce. Libovolnou metodu použijete, rozhraní .NET Framework poskytuje funkce pro kreslení vlastní grafické rozhraní pro libovolný ovládací prvek, který vytvoříte.  
  
 Vykreslování ovládacího prvku provádí spuštění kódu v ovládacím prvku <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. Jeden argument <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda <xref:System.Windows.Forms.PaintEventArgs> objektu, který obsahuje všechny informace a funkce vyžadovaná k vykreslení ovládacího prvku. <xref:System.Windows.Forms.PaintEventArgs> Poskytuje jako vlastnosti dva hlavní objekty, které se použijí při vykreslování ovládacího prvku:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objekt - obdélníku, která reprezentuje část ovládací prvek, který budou vykreslovat. To může být celý ovládací prvek, nebo její část ovládacího prvku v závislosti na tom, jak se nevykreslí ovládacího prvku.  
  
-   <xref:System.Drawing.Graphics>objekt - zapouzdří několik orientované grafické objekty a metody, které poskytují funkce, které jsou potřebné k vykreslení ovládacího prvku.  
  
 Další informace o <xref:System.Drawing.Graphics> objekt a jak ho použít, najdete v části [postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Událost je aktivována vždy, když je ovládací prvek vykreslovat nebo aktualizovat na obrazovce a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt představuje obdélníku, ve kterém bude Malování probíhat. Pokud celý ovládací prvek, je potřeba aktualizovat, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude reprezentovat velikost celý ovládací prvek. Pokud jenom část ovládacího prvku, je potřeba aktualizovat, ale <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objektů bude představovat pouze oblast, která musí být překreslen. Příkladem takové případě může být kdy ovládacího prvku byla částečně zakrytý jiného ovládacího prvku nebo formuláře v uživatelském rozhraní.  
  
 Když je zděděný z <xref:System.Windows.Forms.Control> třídy, je nutné přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a poskytnout grafiky vykreslování kódu v rámci. Pokud chcete zadat vlastní grafické rozhraní pro uživatelský ovládací prvek nebo ovládací prvek zděděné, můžete provést také tak přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. Níže je uveden příklad:  
  
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
  
 Předchozí příklad ukazuje, jak k vykreslení ovládacího prvku s velmi jednoduché grafické reprezentace. Zavolá <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy, vytvoří <xref:System.Drawing.Pen> objektu, ke které má být kreslení a nakonec nakreslí na elipsy v obdélníku dáno <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku. I když většina vykreslování kód bude výrazně složitější než to, tento příklad ukazuje použití <xref:System.Drawing.Graphics> objektů obsažených v rámci <xref:System.Windows.Forms.PaintEventArgs> objektu. Všimněte si, že pokud se dědí z třídy, která již má grafické reprezentace, jako například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>a nechcete, aby k této reprezentace začlenit do vaší vykreslování, by neměla volat základní třída <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.  
  
 Kód <xref:System.Windows.Forms.Control.OnPaint%2A> metoda ovládacího prvku, budou spuštěny při první vykreslením ovládacího prvku a vždy, když je aktualizována. Aby se zajistilo, že vlastní ovládací prvek bude překreslen pokaždé, když se změnila velikost, přidejte následující řádek do konstruktoru objektu vlastního ovládacího prvku:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Použití <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnost implementaci obdélníkový ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Základní ovládací prvky](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
