---
title: 'Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: 671075973793d7fbf0b70ce77428a0a632305b9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941333"
---
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="ef5aa-102">Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ef5aa-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="ef5aa-103">V dřívějších verzích rozhraní .NET Framework, ovládací prvky nepodporoval nastavení transparentní backcolors bez první nastavení <xref:System.Windows.Forms.Control.SetStyle%2A> metoda v konstruktoru formulářích.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="ef5aa-104">V aktuální verzi rozhraní framework backcolor pro většinu ovládacích prvků lze nastavit na <xref:System.Drawing.Color.Transparent%2A> v **vlastnosti** okno v době návrhu nebo v kódu v konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef5aa-105">Ovládací prvky Windows Forms nepodporují true průhlednost.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="ef5aa-106">Na pozadí ovládacího prvku Windows Forms transparentní kresleno svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef5aa-107"><xref:System.Windows.Controls.Button> Ovládací prvek nepodporuje průhlednou barvu backcolor i v případě <xref:System.Windows.Forms.ButtonBase.BackColor%2A> je nastavena na <xref:System.Drawing.Color.Transparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef5aa-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="ef5aa-108">Poskytnout průhlednou barvu backcolor ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ef5aa-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="ef5aa-109">V okně Vlastnosti zvolte <xref:System.Windows.Forms.ButtonBase.BackColor%2A> vlastnost a nastavte ho na <xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="ef5aa-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5aa-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef5aa-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="ef5aa-111">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ef5aa-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="ef5aa-112">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="ef5aa-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="ef5aa-113">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="ef5aa-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
