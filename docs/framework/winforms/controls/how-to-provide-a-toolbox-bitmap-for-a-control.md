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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e6da7318ba481af721a9220c8f71af2a18e764a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015788"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="48f20-102">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="48f20-102">How to: Provide a Toolbox Bitmap for a Control</span></span>

<span data-ttu-id="48f20-103">Pokud chcete mít speciální ikonu pro ovládací prvek, který se zobrazí v **sadě nástrojů** sady Visual Studio, můžete zadat konkrétní obrázek pomocí <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="48f20-103">If you want to have a special icon for your control appear in the **Toolbox** of Visual Studio, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="48f20-104">Tato třída je *atributem*, speciální druh třídy, kterou lze připojit k jiným třídám.</span><span class="sxs-lookup"><span data-stu-id="48f20-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="48f20-105">Další informace o atributech naleznete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pro Visual Basic nebo [atributyC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pro. C#</span><span class="sxs-lookup"><span data-stu-id="48f20-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>

<span data-ttu-id="48f20-106"><xref:System.Drawing.ToolboxBitmapAttribute>Pomocí můžete zadat řetězec, který označuje cestu a název souboru rastrového obrázku o velikosti 16 až 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="48f20-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="48f20-107">Tento rastrový obrázek se pak zobrazí vedle ovládacího prvku, když se přidá do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="48f20-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="48f20-108">Můžete také zadat a <xref:System.Type>, v takovém případě je načten rastrový obrázek přidružený k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="48f20-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="48f20-109">Zadáte- <xref:System.Type> li i řetězec, ovládací prvek vyhledá prostředek obrázku s názvem určeným parametrem řetězce v sestavení, které obsahuje typ určený <xref:System.Type> parametrem.</span><span class="sxs-lookup"><span data-stu-id="48f20-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="48f20-110">Určení rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="48f20-110">To specify a Toolbox bitmap for your control</span></span>

1. <span data-ttu-id="48f20-111">Přidejte do deklarace třídy ovládacího prvku `Class` před klíčovým slovem jazyka Visual Basic a nad deklarací třídy pro vizuál. C# <xref:System.Drawing.ToolboxBitmapAttribute></span><span class="sxs-lookup"><span data-stu-id="48f20-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>

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

2. <span data-ttu-id="48f20-112">Znovu sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="48f20-112">Rebuild the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="48f20-113">Rastr se nezobrazí v sadě nástrojů pro automaticky vygenerované ovládací prvky a součásti.</span><span class="sxs-lookup"><span data-stu-id="48f20-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="48f20-114">Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="48f20-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="48f20-115">Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="48f20-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="48f20-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48f20-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="48f20-117">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="48f20-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="48f20-118">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="48f20-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="48f20-119">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48f20-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="48f20-120">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="48f20-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
