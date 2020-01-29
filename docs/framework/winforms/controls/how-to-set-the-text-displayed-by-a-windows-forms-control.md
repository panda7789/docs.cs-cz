---
title: Nastavení textu zobrazovaného ovládacím prvkem
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
ms.openlocfilehash: eb02cbc3b335b0d5856f786b21d1d202cf444211
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738419"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="fc968-102">Postupy: nastavení textu zobrazovaného ovládacím prvkem model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc968-102">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="fc968-103">Ovládací prvky model Windows Forms obvykle zobrazují nějaký text, který souvisí s primární funkcí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fc968-103">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="fc968-104">Například ovládací prvek <xref:System.Windows.Forms.Button> obvykle zobrazuje titulek, který indikuje, jakou akci bude proveden při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fc968-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="fc968-105">Pro všechny ovládací prvky můžete nastavit nebo vrátit text pomocí vlastnosti <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc968-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="fc968-106">Písmo můžete změnit pomocí vlastnosti <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc968-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="fc968-107">Text můžete také nastavit pomocí [Návrháře](#designer).</span><span class="sxs-lookup"><span data-stu-id="fc968-107">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="fc968-108">Blokují</span><span class="sxs-lookup"><span data-stu-id="fc968-108">Programmatic</span></span>

1. <span data-ttu-id="fc968-109">Vlastnost <xref:System.Windows.Forms.Control.Text%2A> nastavte na řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc968-109">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="fc968-110">K vytvoření podtrženého přístupového klíče obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="fc968-110">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="fc968-111">Nastavte vlastnost <xref:System.Windows.Forms.Control.Font%2A> na objekt typu <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="fc968-111">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

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
    > <span data-ttu-id="fc968-112">Můžete použít řídicí znak pro zobrazení speciálního znaku v prvcích uživatelského rozhraní, které by je obvykle interpretoval jinak, například položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc968-112">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="fc968-113">Například následující řádek kódu nastaví text položky nabídky pro čtení "& nyní pro něco jiného":</span><span class="sxs-lookup"><span data-stu-id="fc968-113">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="fc968-114">Návrhář</span><span class="sxs-lookup"><span data-stu-id="fc968-114">Designer</span></span>

1. <span data-ttu-id="fc968-115">V okně **vlastnosti** v sadě Visual Studio nastavte vlastnost **text** ovládacího prvku na příslušný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc968-115">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="fc968-116">Chcete-li vytvořit podtrženou klávesovou zkratku, zahrnuje ampersand (&) před písmenem, které bude klávesovou zkratkou.</span><span class="sxs-lookup"><span data-stu-id="fc968-116">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="fc968-117">V okně **vlastnosti** vyberte tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti **Font** .</span><span class="sxs-lookup"><span data-stu-id="fc968-117">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="fc968-118">V dialogovém okně standardní písmo vyberte písmo, styl písma, velikost, efekty (například přeškrtnutí nebo podtržení) a požadovaný skript.</span><span class="sxs-lookup"><span data-stu-id="fc968-118">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc968-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc968-119">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fc968-120">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc968-120">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="fc968-121">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fc968-121">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
