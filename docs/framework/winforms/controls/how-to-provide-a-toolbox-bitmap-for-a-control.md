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
ms.openlocfilehash: 3698d2fdbd0375d0a154d6ecea3a248b31da2aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek
Pokud chcete mít speciální ikonu pro ovládací prvek zobrazí v **sada nástrojů**, můžete zadat určitou bitovou kopii pomocí <xref:System.Drawing.ToolboxBitmapAttribute>. Tato třída je *atribut*, zvláštní druh třídy můžete připojit k jiné třídy. Další informace o atributech najdete v tématu [NOT IN sestavení: Přehled atributy v jazyce Visual Basic](http://msdn.microsoft.com/library/0d0cff64-892d-4f57-83bd-bef388553d4f) jazyka Visual Basic a [atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) pro Visual C#.  
  
 Pomocí <xref:System.Drawing.ToolboxBitmapAttribute>, můžete zadat řetězec, který označuje název a cesta k souboru pro rastrový obrázek 16 × 16 pixelů. Tento rastrový obrázek se pak zobrazí vedle vlastního ovládacího prvku, když je přidán do **sada nástrojů**. Můžete také zadat <xref:System.Type>, v takovém případě je načtena rastrový obrázek přidružených k tomuto typu. Pokud zadáte oba <xref:System.Type> a řetězec, ovládacího prvku hledá prostředek obrázku s názvem zadaným parametrem řetězec v sestavení obsahující v typu zadaném pomocí <xref:System.Type> parametr.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Chcete-li určit rastrového obrázku panelu nástrojů pro ovládací prvek  
  
1.  Přidat <xref:System.Drawing.ToolboxBitmapAttribute> k deklaraci třídy ovládacího prvku před `Class` – klíčové slovo jazyka visual Basic a nad deklaraci třídy pro Visual C#.  
  
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
  
2.  Znovu sestavte projekt.  
  
    > [!NOTE]
    >  Bitmapy se nezobrazí v sadě nástrojů pro ovládací prvky generován automaticky a součásti. Informace o bitové mapy, znovu načíst ovládacího prvku pomocí **výběr položek sady nástrojů** dialogové okno. Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.ToolboxBitmapAttribute>  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [Vývoj ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Atributy (Visual Basic)](~/docs/visual-basic/language-reference/attributes.md)  
 [Atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
