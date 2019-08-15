---
title: 'Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039524"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="00424-102">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="00424-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="00424-103">*Přístupový klíč* je podtržený znak v textu nabídky, položky nabídky nebo popisku ovládacího prvku, jako je tlačítko.</span><span class="sxs-lookup"><span data-stu-id="00424-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="00424-104">Umožňuje uživateli "kliknout na tlačítko" stisknutím klávesy ALT v kombinaci s předdefinovaným přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="00424-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="00424-105">Například Pokud tlačítko spustí proceduru pro tisk formuláře, a proto je jeho `Text` vlastnost nastavena na "Tisk", přidání ampersandu (&) před písmenem "p" způsobí, že písmeno "p" bude v textu tlačítka v době běhu podtrženo.</span><span class="sxs-lookup"><span data-stu-id="00424-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="00424-106">Uživatel může spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P.</span><span class="sxs-lookup"><span data-stu-id="00424-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="00424-107">Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.</span><span class="sxs-lookup"><span data-stu-id="00424-107">You cannot have an access key for a control that cannot receive focus.</span></span>

## <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="00424-108">Vytvoření přístupového klíče pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="00424-108">To create an access key for a control</span></span>

1. <span data-ttu-id="00424-109">V okně **vlastnosti** nastavte `Text` vlastnost na řetězec, který obsahuje ampersand (&) před písmenem, který bude přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="00424-109">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="00424-110">Chcete-li například nastavit písmeno "P" jako přístupový klíč, zadejte **& tisk** do mřížky.</span><span class="sxs-lookup"><span data-stu-id="00424-110">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>

## <a name="see-also"></a><span data-ttu-id="00424-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00424-111">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="00424-112">Postupy: Reakce na model Windows Forms kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="00424-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="00424-113">Postupy: Nastavení textu zobrazovaného ovládacím prvkem model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00424-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="00424-114">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="00424-114">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
