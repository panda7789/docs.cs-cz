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
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek
Pokud chcete mít speciální ikonu ovládacího prvku se zobrazí v **nástrojů**, můžete zadat pomocí konkrétní image <xref:System.Drawing.ToolboxBitmapAttribute>. Tato třída je *atribut*, zvláštním druhem třídy lze připojit k jiné třídy. Další informace o atributech najdete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) v jazyce Visual Basic nebo [atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) pro jazyk C#.  
  
 Použití <xref:System.Drawing.ToolboxBitmapAttribute>, můžete zadat řetězec, který určuje název a cesta k souboru rastrového obrázku 16 × 16 pixelů. Tento rastrový obrázek se pak objeví vedle vašeho ovládacího prvku, když se přidá **nástrojů**. Můžete také určit <xref:System.Type>, v takovém případě je načtena rastrový obrázek přidružený k typu. Pokud zadáte oba <xref:System.Type> a řetězec, ovládací prvek vyhledá obrázkový prostředek s názvem zadaným parametrem řetězce v sestavení obsahující typ zadaný <xref:System.Type> parametru.  
  
### <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Chcete-li určit rastrového obrázku panelu nástrojů pro ovládací prvek  
  
1.  Přidat <xref:System.Drawing.ToolboxBitmapAttribute> deklarace třídy ovládacího prvku před `Class` – klíčové slovo v jazyce visual Basic a nad deklaraci třídy pro jazyk Visual C#.  
  
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
  
2.  Sestavte projekt znovu.  
  
    > [!NOTE]
    >  Rastrový obrázek se nezobrazí v sadě nástrojů pro automaticky generované ovládacích prvků a komponent. Rastrový obrázek zobrazíte načtěte pomocí ovládacího prvku **zvolit položky nástrojů** dialogové okno. Další informace najdete v tématu [návod: Automatické vyplnění sady nástrojů pomocí vlastních komponent](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
