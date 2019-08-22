---
title: 'Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms'
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
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666158"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Postupy: Nastavení textu zobrazovaného ovládacím prvkem model Windows Forms

Ovládací prvky model Windows Forms obvykle zobrazují nějaký text, který souvisí s primární funkcí ovládacího prvku. Například <xref:System.Windows.Forms.Button> ovládací prvek obvykle zobrazuje titulek označující akci, která bude provedena při kliknutí na tlačítko. Pro všechny ovládací prvky můžete nastavit nebo vrátit text pomocí <xref:System.Windows.Forms.Control.Text%2A> vlastnosti. Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnosti.

Text můžete také nastavit pomocí [Návrháře](#designer).

## <a name="programmatic"></a>Blokují

1. <xref:System.Windows.Forms.Control.Text%2A> Nastavte vlastnost na řetězec.

   K vytvoření podtrženého přístupového klíče obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem.

2. Nastavte vlastnost na objekt typu <xref:System.Drawing.Font>. <xref:System.Windows.Forms.Control.Font%2A>

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

## <a name="designer"></a>Návrhář

1. V okně **vlastnosti** v sadě Visual Studio nastavte vlastnost **text** ovládacího prvku na příslušný řetězec.

   Chcete-li vytvořit podtrženou klávesovou zkratku, zahrnuje ampersand (&) před písmenem, které bude klávesovou zkratkou.

2. V okně **vlastnosti** vyberte tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady](./media/visual-studio-ellipsis-button.png)Visual Studio) vedle vlastnosti **Font** .

   V dialogovém okně standardní písmo vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a požadovaný skript.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Postupy: Vytvoření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Postupy: Reakce na model Windows Forms kliknutí na tlačítko](how-to-respond-to-windows-forms-button-clicks.md)
