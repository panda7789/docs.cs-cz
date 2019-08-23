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
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966488"
---
# <a name="user-drawn-controls"></a>Ovládací prvky vykreslované uživatelem
.NET Framework poskytuje možnost snadného vývoje vlastních ovládacích prvků. Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků, které jsou vázány pomocí kódu, nebo můžete navrhnout vlastní ovládací prvek od základu. Dědičnost můžete dokonce použít k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a jeho přidáním do své vlastní funkce. Bez ohledu na to, kterou metodu použijete, .NET Framework poskytuje funkce pro nakreslení vlastního grafického rozhraní pro jakýkoli ovládací prvek, který vytvoříte.  
  
 Malování ovládacího prvku je provedeno spuštěním kódu v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku. Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody <xref:System.Windows.Forms.PaintEventArgs> je objekt, který poskytuje všechny informace a funkce požadované pro vykreslení ovládacího prvku. <xref:System.Windows.Forms.PaintEventArgs> Poskytuje jako vlastnosti dva objekty zabezpečení, které budou použity při vykreslování ovládacího prvku:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object – obdélník, který představuje část ovládacího prvku, který bude vykreslen. Může to být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak je ovládací prvek vykreslen.  
  
- <xref:System.Drawing.Graphics>objekt – zapouzdřuje několik grafických objektů a metod, které poskytují funkcionalitu nutnou k nakreslení ovládacího prvku.  
  
 Další informace o <xref:System.Drawing.Graphics> objektu a jeho použití naleznete v tématu [How to: Vytvoření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 Událost se aktivuje vždy, když se ovládací prvek vykreslí nebo aktualizuje na obrazovce <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> a objekt představuje obdélník, ve kterém bude provedeno malování. <xref:System.Windows.Forms.Control.OnPaint%2A> Pokud je nutné celý ovládací prvek aktualizovat, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude reprezentovat velikost celého ovládacího prvku. Je-li však <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nutné aktualizovat pouze část ovládacího prvku, bude objekt představovat pouze oblast, která je zapotřebí překreslit. Příkladem takového případu by bylo, že ovládací prvek byl částečně skryt jiným ovládacím prvkem nebo formulářem v uživatelském rozhraní.  
  
 Při dědění z <xref:System.Windows.Forms.Control> třídy je nutné <xref:System.Windows.Forms.Control.OnPaint%2A> přepsat metodu a zadat kód pro vykreslování grafiky v rámci. Pokud chcete zadat vlastní grafické rozhraní pro uživatelský ovládací prvek nebo Zděděný ovládací prvek, můžete to provést také přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Příklad je uveden níže:  
  
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
  
 Předchozí příklad ukazuje, jak vykreslit ovládací prvek pomocí velmi jednoduché grafické reprezentace. Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu základní třídy, <xref:System.Drawing.Pen> vytvoří objekt, který se má kreslit, a nakonec nakreslí elipsu v obdélníku určeném <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku. I když je většina vykreslování kódu podstatně složitější, tento příklad ukazuje použití <xref:System.Drawing.Graphics> objektu obsaženého <xref:System.Windows.Forms.PaintEventArgs> v objektu. Všimněte si, že pokud dědíte z třídy, která již obsahuje grafické znázornění, například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>, a nechcete začlenit tuto reprezentaci do vykreslování, neměli byste <xref:System.Windows.Forms.Control.OnPaint%2A> volat třídu základní třídy. Metoda.  
  
 Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku bude proveden při prvním vykreslení ovládacího prvku a při každém jeho aktualizaci. Chcete-li zajistit, aby byl ovládací prvek překreslen při každé změně velikosti, přidejte následující řádek do konstruktoru ovládacího prvku:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> Použijte vlastnost k implementaci ovládacího prvku, který není pravoúhlý.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Postupy: Vytvoření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Základní ovládací prvky](constituent-controls.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
