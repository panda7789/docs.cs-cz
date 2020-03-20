---
title: Základní ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182418"
---
# <a name="constituent-controls"></a>Základní ovládací prvky
Ovládací prvky, které tvoří uživatelský ovládací prvek nebo *základní ovládací prvky,* jak jsou označovány, jsou relativně nepružné, pokud jde o vlastní vykreslování grafiky. Všechny ovládací prvky Windows Forms <xref:System.Windows.Forms.Control.OnPaint%2A> zpracovávají vlastní vykreslování vlastní metodou. Vzhledem k tomu, že tato metoda je chráněna, není přístupná vývojáři, a proto nemůže být zabráněno spuštění při vykreslení ovládacího prvku. To však neznamená, že nelze přidat kód ovlivnit vzhled základních ovládacích prvků. Další vykreslování lze provést přidáním obslužné rutiny události. Předpokládejme například, že <xref:System.Windows.Forms.UserControl> jste vytvářeli `MyButton`tlačítko s názvem . Pokud jste chtěli mít další vykreslování nad rámec <xref:System.Web.UI.WebControls.Button>toho, co bylo poskytnuto , byste přidat kód do uživatelského ovládacího prvku podobně jako následující:  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> Některé ovládací prvky <xref:System.Windows.Forms.TextBox>windows forms, například , jsou malovány přímo systémem Windows. V těchto případech <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je nikdy volána, a proto výše uvedený příklad nikdy být volána.  
  
 Tím se vytvoří metoda, která `MyButton.Paint` se spustí při každém spuštění události, čímž se přidá další grafické znázornění ovládacího prvku. Všimněte si, že to `MyButton.OnPaint`nebrání provedení , a proto všechny malování obvykle provádí tlačítko bude stále provedena kromě vlastní malování. Podrobnosti o technologii GDI+ a vlastním vykreslování naleznete v [tématu Vytváření grafických obrazů pomocí technologie GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md). Pokud chcete mít jedinečnou reprezentaci ovládacího prvku, nejlepší postup je vytvořit zděděný ovládací prvek a napsat vlastní vykreslování kód pro něj. Podrobnosti naleznete v [tématu User-Drawn Controls](user-drawn-controls.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Ovládací prvky vykreslované uživatelem](user-drawn-controls.md)
- [Postupy: Vytváření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Typy vlastních ovládacích prvků](varieties-of-custom-controls.md)
