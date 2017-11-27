---
title: "Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="e3830-102">Postupy: Vytváření přístupových klíčů pro ovládací prvky Windows Forms pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="e3830-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="e3830-103">*Přístupový klíč* je podrženého znaku v textu nabídky, položku nabídky nebo popisek ovládací prvek tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e3830-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="e3830-104">Umožňuje uživateli "tlačítko" stisknutím klávesy ALT v kombinaci s předdefinované přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="e3830-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="e3830-105">Například, pokud tlačítko spustí postup tisk formuláře a proto jeho `Text` je nastavena na "Tisk" přidáte ampersand (&) před písmenem "P" způsobí písmenem "P" podtržení text tlačítka v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e3830-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="e3830-106">Uživatele můžete spustit příkaz přidružené tlačítko stisknutím ALT + P.</span><span class="sxs-lookup"><span data-stu-id="e3830-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="e3830-107">Nemůže mít přístupový klíč pro ovládací prvek, který nemůže přijmout fokus.</span><span class="sxs-lookup"><span data-stu-id="e3830-107">You cannot have an access key for a control that cannot receive focus.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3830-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="e3830-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e3830-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e3830-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e3830-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e3830-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="e3830-111">Chcete-li vytvořit přístupový klíč pro ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e3830-111">To create an access key for a control</span></span>  
  
1.  <span data-ttu-id="e3830-112">V **vlastnosti** nastavte `Text` vlastnost na řetězec, který obsahuje znak ampersand (&) před písmeno, které bude přístupový klíč.</span><span class="sxs-lookup"><span data-stu-id="e3830-112">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="e3830-113">Například pokud chcete nastavit písmenem "P" jako přístupový klíč, zadejte **& Tisk** v mřížce.</span><span class="sxs-lookup"><span data-stu-id="e3830-113">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3830-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3830-114">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="e3830-115">Postupy: reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3830-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="e3830-116">Postupy: nastavení textu zobrazovaného prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3830-116">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="e3830-117">Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto</span><span class="sxs-lookup"><span data-stu-id="e3830-117">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
