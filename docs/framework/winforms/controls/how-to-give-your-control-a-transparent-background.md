---
title: "Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ec2c353a960626c54c05009393bcd80dac1b38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek
V dřívějších verzích rozhraní .NET Framework, ovládací prvky nepodporovala nastavení transparentní backcolors bez první nastavení <xref:System.Windows.Forms.Control.SetStyle%2A> metoda v konstruktoru pro formuláře. V aktuální verzi, barva pozadí pro většinu ovládacích prvků může být nastaven na <xref:System.Drawing.Color.Transparent%2A> v **vlastnosti** okno v době návrhu nebo v kódu v konstruktoru formuláře.  
  
> [!NOTE]
>  Ovládací prvky Windows Forms nepodporují true průhlednost. Vykreslení pozadí ovládacího prvku Windows Forms transparentní podle jeho nadřazený objekt.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Řízení nepodporuje průhledná barva pozadí i v případě <xref:System.Windows.Forms.ButtonBase.BackColor%2A> je nastavena na <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Průhledná barva pozadí umožnit vlastního ovládacího prvku  
  
-   V okně vlastností zvolte <xref:System.Windows.Forms.ButtonBase.BackColor%2A> vlastnost a nastavte ji na<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Vývoj vlastních Windows Forms – ovládací prvky s rozhraním .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Postupy: kreslení neprůhledných a poloprůhledných čar](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
