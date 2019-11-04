---
title: 'Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 61f60aaeab904dff80408a1dc46c2882fb5e22b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458322"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="b83c8-102">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b83c8-102">How to: Provide a Toolbox Bitmap for a Control</span></span>

<span data-ttu-id="b83c8-103">Pokud chcete mít speciální ikonu pro ovládací prvek, který se zobrazí v **sadě nástrojů** sady Visual Studio, můžete určit konkrétní obrázek pomocí <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b83c8-103">If you want to have a special icon for your control appear in the **Toolbox** of Visual Studio, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="b83c8-104">Tato třída je *atributem*, speciální druh třídy, kterou lze připojit k jiným třídám.</span><span class="sxs-lookup"><span data-stu-id="b83c8-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="b83c8-105">Další informace o atributech naleznete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pro Visual Basic nebo [atributyC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pro. C#</span><span class="sxs-lookup"><span data-stu-id="b83c8-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>

<span data-ttu-id="b83c8-106">Pomocí <xref:System.Drawing.ToolboxBitmapAttribute>můžete zadat řetězec, který označuje cestu a název souboru pro rastrový obrázek o velikosti 16 až 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="b83c8-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="b83c8-107">Tento rastrový obrázek se pak zobrazí vedle ovládacího prvku, když se přidá do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="b83c8-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="b83c8-108">Můžete také zadat <xref:System.Type>. v takovém případě se načte rastrový obrázek přidružený k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="b83c8-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="b83c8-109">Pokud zadáte <xref:System.Type> i řetězec, ovládací prvek vyhledá prostředek obrázku s názvem určeným parametrem řetězce v sestavení, které obsahuje typ určený parametrem <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b83c8-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="b83c8-110">Určení rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b83c8-110">To specify a Toolbox bitmap for your control</span></span>

1. <span data-ttu-id="b83c8-111">Přidejte <xref:System.Drawing.ToolboxBitmapAttribute> do deklarace třídy ovládacího prvku před klíčovým slovem `Class` pro jazyk Visual Basic a nad deklarací třídy pro vizuál C#.</span><span class="sxs-lookup"><span data-stu-id="b83c8-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>

    ```vb
    ' Specifies the bitmap associated with the Button type.
    <ToolboxBitmap(GetType(Button))> Class MyControl1
    ' Specifies a bitmap file.
    End Class
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _
       Class MyControl2
    End Class
    ' Specifies a type that indicates the assembly to search, and the name
    ' of an image resource to look for.
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl
    End Class
    ```

    ```csharp
    // Specifies the bitmap associated with the Button type.
    [ToolboxBitmap(typeof(Button))]
    class MyControl1 : UserControl
    {
    }
    // Specifies a bitmap file.
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]
    class MyControl2 : UserControl
    {
    }
    // Specifies a type that indicates the assembly to search, and the name
    // of an image resource to look for.
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]
    class MyControl : UserControl
    {
    }
    ```

2. <span data-ttu-id="b83c8-112">Znovu sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="b83c8-112">Rebuild the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b83c8-113">Rastr se nezobrazí v sadě nástrojů pro automaticky vygenerované ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="b83c8-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="b83c8-114">Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="b83c8-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="b83c8-115">Další informace najdete v tématu [Návod: automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="b83c8-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b83c8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b83c8-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="b83c8-117">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="b83c8-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="b83c8-118">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="b83c8-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="b83c8-119">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b83c8-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b83c8-120">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="b83c8-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
