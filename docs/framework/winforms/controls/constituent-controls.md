---
title: "Základní ovládací prvky"
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
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d03b69c334148313b0cd495fad1b2dfd13df833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="constituent-controls"></a>Základní ovládací prvky
Ovládací prvky, které tvoří uživatelský ovládací prvek, nebo *základních ovládacích prvků* jako jsou označovány jako, jsou relativně pevná, pokud jde o vlastní grafiky vykreslování. Všechny ovládací prvky Windows Forms zpracovávat své vlastní vykreslování prostřednictvím svých vlastních <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. Protože tato metoda je chráněn, není přístupná pro vývojáře a proto není možné zabránit spuštění při vykreslení ovládacího prvku. To neznamená, ale, že není možné přidat kód do mají vliv na vzhled základních ovládacích prvků. Další vykreslování dosáhnete přidáním obslužné rutiny události. Předpokládejme například, že byly vytváření obsahu <xref:System.Windows.Forms.UserControl> s tlačítko s názvem `MyButton`. Pokud jste si přáli mít další vykreslování rámec toho, co byl poskytnut <xref:System.Web.UI.WebControls.Button>, byste přidali kód pro váš uživatelský ovládací prvek podobný následujícímu:  
  
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
>  Některé Windows Forms – ovládací prvky, jako například <xref:System.Windows.Forms.TextBox>, jsou vykresluje přímo v systému Windows. V těchto případech <xref:System.Windows.Forms.Control.OnPaint%2A> nikdy metoda je volána, a proto nebude výše uvedeném příkladu nikdy volat.  
  
 Tím se vytvoří metodu, která se spustí pokaždé, když `MyButton.Paint` událost spuštěna, a tím přidání další grafické vyjádření do vlastního ovládacího prvku. Všimněte si, že to nezabrání spuštění `MyButton.OnPaint`, a proto všechny Malování obvykle provádí tlačítko bude stále provést kromě vaše vlastní Malování. Podrobnosti o GDI + technologie a vlastní vykreslení najdete v tématu [vytváření grafického obrázků pomocí GDI +](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Pokud chcete mít jedinečné reprezentace vlastního ovládacího prvku, je váš nejlepší postup k vytvoření ovládacího prvku zděděné a napsat vlastní vykreslení kód pro něj. Podrobnosti najdete v tématu [ovládací prvky User-Drawn](../../../../docs/framework/winforms/controls/user-drawn-controls.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Ovládací prvky vykreslované uživatelem](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Typy vlastních ovládacích prvků](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
