---
title: Účinky úpravy vzhledu základního formuláře
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: a253fef2bc7220d13c0ca373a38a5bf2f5842415
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715552"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="ad7cc-102">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="ad7cc-102">Effects of Modifying a Base Form's Appearance</span></span>
<span data-ttu-id="ad7cc-103">Během vývoje aplikace může často potřeba změnit vzhledu základního formuláře, ze kterého se dědí jiné formuláře v projektu (nebo v jiných projektech).</span><span class="sxs-lookup"><span data-stu-id="ad7cc-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="ad7cc-104">V době návrhu, změny vzhledu základního formuláře (jde o nastavení vlastnosti nebo sčítání a odčítání ovládací prvky), se projeví ve zděděné formuláře při sestavení projektu, který obsahuje základní formulář.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="ad7cc-105">Nestačí jednoduše uložit změny do základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="ad7cc-106">Chcete-li sestavení projektu, zvolte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad7cc-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ad7cc-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ad7cc-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ad7cc-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="ad7cc-110">Změny základního formuláře v době běhu mít žádný vliv na zděděné formuláře, které jsou již vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="ad7cc-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7cc-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad7cc-111">See also</span></span>
- [<span data-ttu-id="ad7cc-112">base</span><span class="sxs-lookup"><span data-stu-id="ad7cc-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="ad7cc-113">Postupy: Dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="ad7cc-113">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="ad7cc-114">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad7cc-114">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
