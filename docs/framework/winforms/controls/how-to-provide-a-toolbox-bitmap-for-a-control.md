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
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Postupy: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek

Pokud chcete mít speciální ikonu pro ovládací prvek, který se zobrazí v **sadě nástrojů** sady Visual Studio, můžete zadat konkrétní obrázek pomocí <xref:System.Drawing.ToolboxBitmapAttribute>. Tato třída je *atributem*, speciální druh třídy, kterou lze připojit k jiným třídám. Další informace o atributech naleznete v tématu [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) pro Visual Basic nebo [atributyC#()](../../../csharp/programming-guide/concepts/attributes/index.md) pro. C#

<xref:System.Drawing.ToolboxBitmapAttribute>Pomocí můžete zadat řetězec, který označuje cestu a název souboru rastrového obrázku o velikosti 16 až 16 pixelů. Tento rastrový obrázek se pak zobrazí vedle ovládacího prvku, když se přidá do **sady nástrojů**. Můžete také zadat a <xref:System.Type>, v takovém případě je načten rastrový obrázek přidružený k tomuto typu. Zadáte- <xref:System.Type> li i řetězec, ovládací prvek vyhledá prostředek obrázku s názvem určeným parametrem řetězce v sestavení, které obsahuje typ určený <xref:System.Type> parametrem.

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Určení rastrového obrázku panelu nástrojů pro ovládací prvek

1. Přidejte do deklarace třídy ovládacího prvku `Class` před klíčovým slovem jazyka Visual Basic a nad deklarací třídy pro vizuál. C# <xref:System.Drawing.ToolboxBitmapAttribute>

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
    > Rastr se nezobrazí v sadě nástrojů pro automaticky vygenerované ovládací prvky a součásti. Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** . Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Přehled atributů (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Atributy (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
