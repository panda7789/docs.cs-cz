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
ms.openlocfilehash: aa32850b9bcd1a15a93bd6c80b2278278d12c417
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746542"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="882d9-102">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="882d9-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="882d9-103">Pokud chcete mít speciální ikonu ovládacího prvku se zobrazí v **nástrojů**, můžete zadat pomocí konkrétní image <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="882d9-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="882d9-104">Tato třída je *atribut*, zvláštním druhem třídy lze připojit k jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="882d9-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="882d9-105">Další informace o atributech najdete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) v jazyce Visual Basic nebo [atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) pro jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="882d9-105">For more information about attributes, see [Attributes overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) for Visual Basic or [Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) for C#.</span></span>  
  
 <span data-ttu-id="882d9-106">Použití <xref:System.Drawing.ToolboxBitmapAttribute>, můžete zadat řetězec, který určuje název a cesta k souboru rastrového obrázku 16 × 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="882d9-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="882d9-107">Tento rastrový obrázek se pak objeví vedle vašeho ovládacího prvku, když se přidá **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="882d9-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="882d9-108">Můžete také určit <xref:System.Type>, v takovém případě je načtena rastrový obrázek přidružený k typu.</span><span class="sxs-lookup"><span data-stu-id="882d9-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="882d9-109">Pokud zadáte oba <xref:System.Type> a řetězec, ovládací prvek vyhledá obrázkový prostředek s názvem zadaným parametrem řetězce v sestavení obsahující typ zadaný <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="882d9-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="882d9-110">Chcete-li určit rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="882d9-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="882d9-111">Přidat <xref:System.Drawing.ToolboxBitmapAttribute> deklarace třídy ovládacího prvku před `Class` – klíčové slovo v jazyce visual Basic a nad deklaraci třídy pro jazyk Visual C#.</span><span class="sxs-lookup"><span data-stu-id="882d9-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for visual Basic, and above the class declaration for Visual C#.</span></span>  
  
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
  
2.  <span data-ttu-id="882d9-112">Sestavte projekt znovu.</span><span class="sxs-lookup"><span data-stu-id="882d9-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="882d9-113">Rastrový obrázek se nezobrazí v sadě nástrojů pro automaticky generované ovládacích prvků a komponent.</span><span class="sxs-lookup"><span data-stu-id="882d9-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="882d9-114">Rastrový obrázek zobrazíte načtěte pomocí ovládacího prvku **zvolit položky nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="882d9-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="882d9-115">Další informace najdete v tématu [návod: Automatické vyplnění sady nástrojů pomocí vlastních komponent](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="882d9-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882d9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="882d9-116">See also</span></span>

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [<span data-ttu-id="882d9-117">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="882d9-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="882d9-118">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="882d9-118">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="882d9-119">Přehled atributů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="882d9-119">Attributes overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="882d9-120">Atributy (C#)</span><span class="sxs-lookup"><span data-stu-id="882d9-120">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
