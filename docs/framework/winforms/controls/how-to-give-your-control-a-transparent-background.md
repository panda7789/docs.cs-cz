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
# <a name="how-to-give-your-control-a-transparent-background"></a><span data-ttu-id="b3286-102">Postupy: Nastavení průhledného pozadí pro vlastní ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b3286-102">How to: Give Your Control a Transparent Background</span></span>
<span data-ttu-id="b3286-103">V dřívějších verzích .NET Framework ovládací prvky nepodporovaly nastavení průhledných BackColor BackColor bez prvotního nastavení <xref:System.Windows.Forms.Control.SetStyle%2A> metody v konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="b3286-103">In earlier versions of the .NET Framework, controls didn't support setting transparent backcolors without first setting the <xref:System.Windows.Forms.Control.SetStyle%2A> method in the forms's constructor.</span></span> <span data-ttu-id="b3286-104">V aktuální verzi rozhraní může být barva BackColor pro většinu ovládacích prvků nastavena na <xref:System.Drawing.Color.Transparent%2A> hodnotu v okně **vlastnosti** v době návrhu nebo v kódu v konstruktoru formuláře.</span><span class="sxs-lookup"><span data-stu-id="b3286-104">In the current framework version, the backcolor for most controls can be set to <xref:System.Drawing.Color.Transparent%2A> in the **Properties** window at design time, or in code in the form's constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3286-105">Ovládací prvky model Windows Forms nepodporují skutečnou průhlednost.</span><span class="sxs-lookup"><span data-stu-id="b3286-105">Windows Forms controls do not support true transparency.</span></span> <span data-ttu-id="b3286-106">Pozadí transparentního ovládacího prvku model Windows Forms je vykresleno jeho nadřazenou položkou.</span><span class="sxs-lookup"><span data-stu-id="b3286-106">The background of a transparent Windows Forms control is painted by its parent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3286-107">Ovládací prvek nepodporuje průhlednou barvu BackColor i v případě, že <xref:System.Windows.Forms.ButtonBase.BackColor%2A> je vlastnost nastavena na <xref:System.Drawing.Color.Transparent%2A>hodnotu. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="b3286-107">The <xref:System.Windows.Controls.Button> control doesn't support a transparent backcolor even when the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property is set to <xref:System.Drawing.Color.Transparent%2A>.</span></span>  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a><span data-ttu-id="b3286-108">Poskytnutí průhledné barvy pozadí vašemu ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="b3286-108">To give your control a transparent backcolor</span></span>  
  
- <span data-ttu-id="b3286-109">V okno Vlastnosti vyberte <xref:System.Windows.Forms.ButtonBase.BackColor%2A> vlastnost a nastavte ji na<xref:System.Drawing.Color.Transparent%2A></span><span class="sxs-lookup"><span data-stu-id="b3286-109">In the Properties window, choose the <xref:System.Windows.Forms.ButtonBase.BackColor%2A> property and set it to <xref:System.Drawing.Color.Transparent%2A></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3286-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3286-110">See also</span></span>

- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="b3286-111">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3286-111">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="b3286-112">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="b3286-112">Using Managed Graphics Classes</span></span>](../advanced/using-managed-graphics-classes.md)
- [<span data-ttu-id="b3286-113">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="b3286-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
