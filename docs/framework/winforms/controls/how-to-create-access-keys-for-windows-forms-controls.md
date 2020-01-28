---
title: Vytváření přístupových klíčů pro ovládací prvky
ms.date: 08/20/2019
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
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731169"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="e733d-102">Postupy: vytváření přístupových klíčů pro model Windows Forms ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="e733d-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="e733d-103">*Přístupový klíč* je podtržený znak v textu nabídky, položky nabídky nebo popisku ovládacího prvku, jako je tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e733d-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="e733d-104">V případě přístupového klíče může uživatel "kliknout" tlačítko stisknutím klávesy ALT v kombinaci s předdefinovaným přístupovým klíčem.</span><span class="sxs-lookup"><span data-stu-id="e733d-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="e733d-105">Například Pokud tlačítko spustí proceduru pro tisk formuláře, a proto je jeho vlastnost `Text` nastavena na "Tisk", přidání ampersandu před písmeno "P" způsobí, že písmeno "P" bude v textu tlačítka v době běhu podtrženo.</span><span class="sxs-lookup"><span data-stu-id="e733d-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="e733d-106">Uživatel může spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P.</span><span class="sxs-lookup"><span data-stu-id="e733d-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="e733d-107">Ovládací prvky, které nemůžou získat fokus, nemůžou mít přístupové klíče.</span><span class="sxs-lookup"><span data-stu-id="e733d-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="e733d-108">Blokují</span><span class="sxs-lookup"><span data-stu-id="e733d-108">Programmatic</span></span>

<span data-ttu-id="e733d-109">Nastavte vlastnost `Text` na řetězec, který obsahuje ampersand (&) před písmenem, které bude zástupcem.</span><span class="sxs-lookup"><span data-stu-id="e733d-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

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
> <span data-ttu-id="e733d-110">Chcete-li v titulku použít ampersand bez vytvoření přístupového klíče, přidejte dva ampersandy (& &).</span><span class="sxs-lookup"><span data-stu-id="e733d-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="e733d-111">V titulku se zobrazí jeden ampersand a žádné znaky nejsou podtržené.</span><span class="sxs-lookup"><span data-stu-id="e733d-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="e733d-112">Návrhář</span><span class="sxs-lookup"><span data-stu-id="e733d-112">Designer</span></span>

<span data-ttu-id="e733d-113">V okně **vlastnosti** sady Visual Studio nastavte vlastnost **text** na řetězec, který obsahuje ampersand (' & ') před písmenem, které bude přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="e733d-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="e733d-114">Chcete-li například nastavit písmeno "P" jako přístupový klíč, zadejte **& tisk**.</span><span class="sxs-lookup"><span data-stu-id="e733d-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="e733d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e733d-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="e733d-116">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e733d-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="e733d-117">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e733d-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="e733d-118">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="e733d-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
