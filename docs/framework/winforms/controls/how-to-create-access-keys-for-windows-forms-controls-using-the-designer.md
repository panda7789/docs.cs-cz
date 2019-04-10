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
ms.openlocfilehash: 900a955173c28c7b86fce73e418561ed437719c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216922"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="71ada-102">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="71ada-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="71ada-103">*Přístupový klíč* je znak podtržený text nabídky, položka nabídky nebo popisek ovládacích prvcích jako tlačítko.</span><span class="sxs-lookup"><span data-stu-id="71ada-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="71ada-104">Umožňuje uživateli "tlačítko" stisknutím klávesy ALT v kombinaci s předdefinovanou přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="71ada-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="71ada-105">Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Tisk," "Přidání znak ampersand (&) před písmeno" P "způsobí, že písmeno"P", chcete-li být podtržená v textu tlačítka v době běhu.</span><span class="sxs-lookup"><span data-stu-id="71ada-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="71ada-106">Uživatele můžete spustit příkaz přidružený k tlačítku stisknutím kombinace kláves ALT + P.</span><span class="sxs-lookup"><span data-stu-id="71ada-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="71ada-107">Nemůžete mít přístupový klíč pro ovládací prvek, který nemůže získat fokus.</span><span class="sxs-lookup"><span data-stu-id="71ada-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71ada-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="71ada-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="71ada-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="71ada-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="71ada-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="71ada-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="71ada-111">Chcete-li vytvořit přístupový klíč pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="71ada-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="71ada-112">V **vlastnosti** okno, nastaveno `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmenem, který bude přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="71ada-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="71ada-113">Například nastavte na písmeno "P" jako přístupový klíč, zadejte **& Tisk** do mřížky.</span><span class="sxs-lookup"><span data-stu-id="71ada-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ada-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71ada-114">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="71ada-115">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71ada-115">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="71ada-116">Postupy: Nastavení textu zobrazovaného ovládacím prvkem Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71ada-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="71ada-117">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="71ada-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
