---
title: 'Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966643"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek
V dřívějších verzích .NET Framework ovládací prvky nepodporovaly nastavení průhledných BackColor BackColor bez prvotního nastavení <xref:System.Windows.Forms.Control.SetStyle%2A> metody v konstruktoru formuláře. V aktuální verzi rozhraní může být barva BackColor pro většinu ovládacích prvků nastavena na <xref:System.Drawing.Color.Transparent%2A> hodnotu v okně **vlastnosti** v době návrhu nebo v kódu v konstruktoru formuláře.  
  
> [!NOTE]
> Ovládací prvky model Windows Forms nepodporují skutečnou průhlednost. Pozadí transparentního ovládacího prvku model Windows Forms je vykresleno jeho nadřazenou položkou.  
  
> [!NOTE]
> Ovládací prvek nepodporuje průhlednou barvu BackColor i v případě, že <xref:System.Windows.Forms.ButtonBase.BackColor%2A> je vlastnost nastavena na <xref:System.Drawing.Color.Transparent%2A>hodnotu. <xref:System.Windows.Controls.Button>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Poskytnutí průhledné barvy pozadí vašemu ovládacímu prvku  
  
- V okno Vlastnosti vyberte <xref:System.Windows.Forms.ButtonBase.BackColor%2A> vlastnost a nastavte ji na<xref:System.Drawing.Color.Transparent%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Color.FromArgb%2A>
- [Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework](developing-custom-windows-forms-controls.md)
- [Použití spravovaných grafických tříd](../advanced/using-managed-graphics-classes.md)
- [Postupy: Kreslení neprůhledných a poloprůhledných čar](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
