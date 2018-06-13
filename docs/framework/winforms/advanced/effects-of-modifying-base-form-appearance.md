---
title: Účinky úpravy základní formulář&#39;s vzhledu
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 7ba4a78395bb93caa1d1d86dc135825ca2a58845
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520549"
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="1bbb3-102">Účinky úpravy základní formulář&#39;s vzhledu</span><span class="sxs-lookup"><span data-stu-id="1bbb3-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="1bbb3-103">Během vývoje aplikace může často potřebujete změnit vzhled základní formulář, ze kterého jsou dědění jiných formulářů v projektu (nebo jiné projekty).</span><span class="sxs-lookup"><span data-stu-id="1bbb3-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="1bbb3-104">V době návrhu, změny vzhledu základního formuláře (ať už, nastavení vlastnosti nebo přidání a odčítání ovládacích prvků) se projeví na zděděné formuláře při sestavení projektu obsahující základní formulář.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="1bbb3-105">Není dostatek můžete jednoduše uložit změny do základní formulář.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="1bbb3-106">Pokud chcete vytvořit projekt, vyberte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bbb3-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1bbb3-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1bbb3-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1bbb3-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
 <span data-ttu-id="1bbb3-110">Změny provedené v době běhu základní formulář mít žádný vliv na zděděné formuláře, které jsou již vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="1bbb3-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbb3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bbb3-111">See Also</span></span>  
 [<span data-ttu-id="1bbb3-112">base</span><span class="sxs-lookup"><span data-stu-id="1bbb3-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="1bbb3-113">Postupy: Dědění v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1bbb3-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="1bbb3-114">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1bbb3-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
