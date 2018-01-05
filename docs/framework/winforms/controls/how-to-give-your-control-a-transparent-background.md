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
ms.workload: dotnet
ms.openlocfilehash: ab2a8562401561cfb2a54d4630e32bf7527da10d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 [Postupy: Kreslení neprůhledných a poloprůhledných čar](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
