---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 1bfbd2c6cd8aae410dfed506437bc85fbcb1d311
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597850"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="4efbf-102">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4efbf-102">How to: Create Access Keys for Windows Forms Controls</span></span>
<span data-ttu-id="4efbf-103">*Přístupový klíč* je znak podtržený text nabídky, položka nabídky nebo popisek ovládacích prvcích jako tlačítko.</span><span class="sxs-lookup"><span data-stu-id="4efbf-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="4efbf-104">Přístupový klíč uživatel může "klikněte" tlačítko stisknutím klávesy ALT v kombinaci s předdefinovanou přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="4efbf-104">With an access key, the user can "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="4efbf-105">Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Print","Přidání ampersand před písmeno"P"způsobí, že písmeno"P", chcete-li být podtržený text tlačítka v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4efbf-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="4efbf-106">Uživatele můžete spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P.</span><span class="sxs-lookup"><span data-stu-id="4efbf-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="4efbf-107">Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.</span><span class="sxs-lookup"><span data-stu-id="4efbf-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="4efbf-108">Chcete-li vytvořit přístupový klíč pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="4efbf-108">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="4efbf-109">Nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmenem, který bude klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="4efbf-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4efbf-110">Vložit znak ampersand titulek bez vytvoření přístupového klíče, zahrnují dva ampersandy (& &).</span><span class="sxs-lookup"><span data-stu-id="4efbf-110">To include an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="4efbf-111">Znak ampersand se zobrazí v záhlaví a žádné znaky jsou podtrženy.</span><span class="sxs-lookup"><span data-stu-id="4efbf-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efbf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4efbf-112">See also</span></span>
- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="4efbf-113">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4efbf-113">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="4efbf-114">Postupy: Nastavit Text, zobrazený ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4efbf-114">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="4efbf-115">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="4efbf-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
