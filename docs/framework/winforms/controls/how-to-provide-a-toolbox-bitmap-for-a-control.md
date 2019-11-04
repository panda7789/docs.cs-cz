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
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek

Pokud chcete mít speciální ikonu pro ovládací prvek, který se zobrazí v **sadě nástrojů** sady Visual Studio, můžete určit konkrétní obrázek pomocí <xref:System.Drawing.ToolboxBitmapAttribute>. Tato třída je *atributem*, speciální druh třídy, kterou lze připojit k jiným třídám. Další informace o atributech naleznete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pro Visual Basic nebo [atributyC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pro. C#

Pomocí <xref:System.Drawing.ToolboxBitmapAttribute>můžete zadat řetězec, který označuje cestu a název souboru pro rastrový obrázek o velikosti 16 až 16 pixelů. Tento rastrový obrázek se pak zobrazí vedle ovládacího prvku, když se přidá do **sady nástrojů**. Můžete také zadat <xref:System.Type>. v takovém případě se načte rastrový obrázek přidružený k tomuto typu. Pokud zadáte <xref:System.Type> i řetězec, ovládací prvek vyhledá prostředek obrázku s názvem určeným parametrem řetězce v sestavení, které obsahuje typ určený parametrem <xref:System.Type>.

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Určení rastrového obrázku panelu nástrojů pro ovládací prvek

1. Přidejte <xref:System.Drawing.ToolboxBitmapAttribute> do deklarace třídy ovládacího prvku před klíčovým slovem `Class` pro jazyk Visual Basic a nad deklarací třídy pro vizuál C#.

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

2. Znovu sestavte projekt.

    > [!NOTE]
    > Rastr se nezobrazí v sadě nástrojů pro automaticky vygenerované ovládací prvky a součásti. Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** . Další informace najdete v tématu [Návod: automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
