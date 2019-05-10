---
title: 'Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 8a03d9afec5340cd77af465c4470b7484b8926be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609706"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek
V dřívějších verzích rozhraní .NET Framework, ovládací prvky nepodporoval nastavení transparentní backcolors bez první nastavení <xref:System.Windows.Forms.Control.SetStyle%2A> metoda v konstruktoru formulářích. V aktuální verzi rozhraní framework backcolor pro většinu ovládacích prvků lze nastavit na <xref:System.Drawing.Color.Transparent%2A> v **vlastnosti** okno v době návrhu nebo v kódu v konstruktoru formuláře.  
  
> [!NOTE]
>  Ovládací prvky Windows Forms nepodporují true průhlednost. Na pozadí ovládacího prvku Windows Forms transparentní kresleno svého nadřazeného objektu.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Button> Ovládací prvek nepodporuje průhlednou barvu backcolor i v případě <xref:System.Windows.Forms.ButtonBase.BackColor%2A> je nastavena na <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Poskytnout průhlednou barvu backcolor ovládacího prvku  
  
- V okně Vlastnosti zvolte <xref:System.Windows.Forms.ButtonBase.BackColor%2A> vlastnost a nastavte ho na <xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Color.FromArgb%2A>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Použití spravovaných grafických tříd](../advanced/using-managed-graphics-classes.md)
- [Postupy: Kreslení neprůhledných a poloprůhledných čar](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
