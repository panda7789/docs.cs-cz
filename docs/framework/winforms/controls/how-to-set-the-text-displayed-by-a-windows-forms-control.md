---
title: 'Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 30cf71aa2a87ff99ccb965844b620ef08a20b69c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636443"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="2214f-102">Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2214f-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="2214f-103">Ovládací prvky Windows Forms obvykle zobrazí text, který souvisí s primární funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2214f-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="2214f-104">Například <xref:System.Windows.Forms.Button> ovládací prvek obvykle zobrazí popisek indikující, jaká akce se provede při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2214f-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="2214f-105">Pro všechny ovládací prvky, můžete nastavit nebo načíst text pomocí <xref:System.Windows.Forms.Control.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2214f-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="2214f-106">Můžete změnit písmo pomocí <xref:System.Windows.Forms.Control.Font%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2214f-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="2214f-107">Můžete také nastavit text pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="2214f-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="2214f-108">Viz také [jak: Vytváření přístupových klíčů pro Windows Forms pomocí návrháře ovládacích prvků](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [jak: Nastavit Text, zobrazený Windows Forms pomocí návrháře ovládací prvek](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [jak: Nastavení obrázku zobrazovaného pomocí ovládacího prvku pomocí Návrháře formulářů Windows](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="2214f-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="2214f-109">K nastavení textu zobrazovaného ovládacím prvkem prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2214f-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="2214f-110">Nastavte <xref:System.Windows.Forms.Control.Text%2A> nastavte na řetězec.</span><span class="sxs-lookup"><span data-stu-id="2214f-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="2214f-111">K vytvoření podtržené přístupový klíč, obsahuje znak ampersand (&) před písmenem, který bude přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="2214f-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="2214f-112">Nastavte <xref:System.Windows.Forms.Control.Font%2A> vlastnost na objekt typu <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="2214f-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2214f-113">Řídicí znak slouží k zobrazení speciálního znaku v prvcích uživatelského rozhraní, které by normálně interpretovat, jako je například položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="2214f-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="2214f-114">Například následující řádek kódu nastaví text položky nabídky ke čtení "& nyní pro něco úplně odlišnému":</span><span class="sxs-lookup"><span data-stu-id="2214f-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2214f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2214f-115">See also</span></span>
- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2214f-116">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2214f-116">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="2214f-117">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2214f-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
