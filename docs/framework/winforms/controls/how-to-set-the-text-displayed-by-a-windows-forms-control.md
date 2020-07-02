---
title: Nastavení textu zobrazovaného ovládacím prvkem
description: Přečtěte si, jak nastavit text zobrazený ovládacím prvkem model Windows Forms. Nastavte nebo vraťte text pomocí vlastnosti text nebo změňte písmo pomocí vlastnosti Font.
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622845"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Postupy: nastavení textu zobrazovaného ovládacím prvkem model Windows Forms

Ovládací prvky model Windows Forms obvykle zobrazují nějaký text, který souvisí s primární funkcí ovládacího prvku. Například <xref:System.Windows.Forms.Button> ovládací prvek obvykle zobrazuje titulek označující akci, která bude provedena při kliknutí na tlačítko. Pro všechny ovládací prvky můžete nastavit nebo vrátit text pomocí <xref:System.Windows.Forms.Control.Text%2A> Vlastnosti. Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> Vlastnosti.

Text můžete také nastavit pomocí [Návrháře](#designer).

## <a name="programmatic"></a>Programová

1. Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na řetězec.

   K vytvoření podtrženého přístupového klíče obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem.

2. Nastavte <xref:System.Windows.Forms.Control.Font%2A> vlastnost na objekt typu <xref:System.Drawing.Font> .

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > Můžete použít řídicí znak pro zobrazení speciálního znaku v prvcích uživatelského rozhraní, které by je obvykle interpretoval jinak, například položky nabídky. Například následující řádek kódu nastaví text položky nabídky pro čtení "& nyní pro něco jiného":

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Designer

1. V okně **vlastnosti** v sadě Visual Studio nastavte vlastnost **text** ovládacího prvku na příslušný řetězec.

   Chcete-li vytvořit podtrženou klávesovou zkratku, zahrnuje ampersand (&) před písmenem, které bude klávesovou zkratkou.

2. V okně **vlastnosti** vyberte tlačítko se třemi tečkami ( ![ tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio ](./media/visual-studio-ellipsis-button.png) ) vedle vlastnosti **Font** .

   V dialogovém okně standardní písmo vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a požadovaný skript.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
