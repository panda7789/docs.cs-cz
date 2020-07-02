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
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="c4721-104">Postupy: nastavení textu zobrazovaného ovládacím prvkem model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4721-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="c4721-105">Ovládací prvky model Windows Forms obvykle zobrazují nějaký text, který souvisí s primární funkcí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c4721-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="c4721-106">Například <xref:System.Windows.Forms.Button> ovládací prvek obvykle zobrazuje titulek označující akci, která bude provedena při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c4721-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="c4721-107">Pro všechny ovládací prvky můžete nastavit nebo vrátit text pomocí <xref:System.Windows.Forms.Control.Text%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4721-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="c4721-108">Písmo můžete změnit pomocí <xref:System.Windows.Forms.Control.Font%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4721-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="c4721-109">Text můžete také nastavit pomocí [Návrháře](#designer).</span><span class="sxs-lookup"><span data-stu-id="c4721-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="c4721-110">Programová</span><span class="sxs-lookup"><span data-stu-id="c4721-110">Programmatic</span></span>

1. <span data-ttu-id="c4721-111">Nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost na řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4721-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="c4721-112">K vytvoření podtrženého přístupového klíče obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="c4721-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="c4721-113">Nastavte <xref:System.Windows.Forms.Control.Font%2A> vlastnost na objekt typu <xref:System.Drawing.Font> .</span><span class="sxs-lookup"><span data-stu-id="c4721-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

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
    > <span data-ttu-id="c4721-114">Můžete použít řídicí znak pro zobrazení speciálního znaku v prvcích uživatelského rozhraní, které by je obvykle interpretoval jinak, například položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="c4721-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="c4721-115">Například následující řádek kódu nastaví text položky nabídky pro čtení "& nyní pro něco jiného":</span><span class="sxs-lookup"><span data-stu-id="c4721-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="c4721-116">Designer</span><span class="sxs-lookup"><span data-stu-id="c4721-116">Designer</span></span>

1. <span data-ttu-id="c4721-117">V okně **vlastnosti** v sadě Visual Studio nastavte vlastnost **text** ovládacího prvku na příslušný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c4721-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="c4721-118">Chcete-li vytvořit podtrženou klávesovou zkratku, zahrnuje ampersand (&) před písmenem, které bude klávesovou zkratkou.</span><span class="sxs-lookup"><span data-stu-id="c4721-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="c4721-119">V okně **vlastnosti** vyberte tlačítko se třemi tečkami ( ![ tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio ](./media/visual-studio-ellipsis-button.png) ) vedle vlastnosti **Font** .</span><span class="sxs-lookup"><span data-stu-id="c4721-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="c4721-120">V dialogovém okně standardní písmo vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a požadovaný skript.</span><span class="sxs-lookup"><span data-stu-id="c4721-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4721-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4721-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c4721-122">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4721-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="c4721-123">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c4721-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
