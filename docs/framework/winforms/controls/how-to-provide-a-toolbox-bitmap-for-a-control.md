---
title: "Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek"
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
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 947ac4f8783b388135cf9e8147bb48eda93cfa08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a><span data-ttu-id="7055a-102">Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7055a-102">How to: Provide a Toolbox Bitmap for a Control</span></span>
<span data-ttu-id="7055a-103">Pokud chcete mít speciální ikonu pro ovládací prvek zobrazí v **sada nástrojů**, můžete zadat určitou bitovou kopii pomocí <xref:System.Drawing.ToolboxBitmapAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7055a-103">If you want to have a special icon for your control appear in the **Toolbox**, you can specify a particular image by using the <xref:System.Drawing.ToolboxBitmapAttribute>.</span></span> <span data-ttu-id="7055a-104">Tato třída je *atribut*, zvláštní druh třídy můžete připojit k jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="7055a-104">This class is an *attribute*, a special kind of class you can attach to other classes.</span></span> <span data-ttu-id="7055a-105">Další informace o atributech najdete v tématu [NOT IN sestavení: Přehled atributy v jazyce Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) pro [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] a [atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) pro [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7055a-105">For more information about attributes, see [NOT IN BUILD: Attributes Overview in Visual Basic](http://msdn.microsoft.com/en-us/0d0cff64-892d-4f57-83bd-bef388553d4f) for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] and [Attributes](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
 <span data-ttu-id="7055a-106">Pomocí <xref:System.Drawing.ToolboxBitmapAttribute>, můžete zadat řetězec, který označuje název a cesta k souboru pro rastrový obrázek 16 × 16 pixelů.</span><span class="sxs-lookup"><span data-stu-id="7055a-106">Using the <xref:System.Drawing.ToolboxBitmapAttribute>, you can specify a string that indicates the path and file name for a 16 by 16 pixel bitmap.</span></span> <span data-ttu-id="7055a-107">Tento rastrový obrázek se pak zobrazí vedle vlastního ovládacího prvku, když je přidán do **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="7055a-107">This bitmap then appears next to your control when added to the **Toolbox**.</span></span> <span data-ttu-id="7055a-108">Můžete také zadat <xref:System.Type>, v takovém případě je načtena rastrový obrázek přidružených k tomuto typu.</span><span class="sxs-lookup"><span data-stu-id="7055a-108">You can also specify a <xref:System.Type>, in which case the bitmap associated with that type is loaded.</span></span> <span data-ttu-id="7055a-109">Pokud zadáte oba <xref:System.Type> a řetězec, ovládacího prvku hledá prostředek obrázku s názvem zadaným parametrem řetězec v sestavení obsahující v typu zadaném pomocí <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="7055a-109">If you specify both a <xref:System.Type> and a string, the control searches for an image resource with the name specified by the string parameter in the assembly containing the type specified by the <xref:System.Type> parameter.</span></span>  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a><span data-ttu-id="7055a-110">Chcete-li určit rastrového obrázku panelu nástrojů pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7055a-110">To specify a Toolbox bitmap for your control</span></span>  
  
1.  <span data-ttu-id="7055a-111">Přidat <xref:System.Drawing.ToolboxBitmapAttribute> k deklaraci třídy ovládacího prvku před `Class` – klíčové slovo pro [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]a nad deklaraci třídy pro [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7055a-111">Add the <xref:System.Drawing.ToolboxBitmapAttribute> to the class declaration of your control before the `Class` keyword for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], and above the class declaration for [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)].</span></span>  
  
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
  
2.  <span data-ttu-id="7055a-112">Znovu sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="7055a-112">Rebuild the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7055a-113">Bitmapy se nezobrazí v sadě nástrojů pro ovládací prvky generován automaticky a součásti.</span><span class="sxs-lookup"><span data-stu-id="7055a-113">The bitmap does not appear in the Toolbox for autogenerated controls and components.</span></span> <span data-ttu-id="7055a-114">Informace o bitové mapy, znovu načíst ovládacího prvku pomocí **výběr položek sady nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7055a-114">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="7055a-115">Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="7055a-115">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7055a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7055a-116">See Also</span></span>  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [<span data-ttu-id="7055a-117">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="7055a-117">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="7055a-118">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="7055a-118">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="7055a-119">Atributy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7055a-119">Attributes (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="7055a-120">Atributy</span><span class="sxs-lookup"><span data-stu-id="7055a-120">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
