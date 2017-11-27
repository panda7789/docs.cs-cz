---
title: "Účinky úpravy základní formulář & č. 39; s vzhledu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1e0eb19946ef2231b5a58df4b8d0b2e40e8e99f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="effects-of-modifying-a-base-form39s-appearance"></a><span data-ttu-id="71549-102">Účinky úpravy základní formulář & č. 39; s vzhledu</span><span class="sxs-lookup"><span data-stu-id="71549-102">Effects of Modifying a Base Form&#39;s Appearance</span></span>
<span data-ttu-id="71549-103">Během vývoje aplikace může často potřebujete změnit vzhled základní formulář, ze kterého jsou dědění jiných formulářů v projektu (nebo jiné projekty).</span><span class="sxs-lookup"><span data-stu-id="71549-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="71549-104">V době návrhu, změny vzhledu základního formuláře (ať už, nastavení vlastnosti nebo přidání a odčítání ovládacích prvků) se projeví na zděděné formuláře při sestavení projektu obsahující základní formulář.</span><span class="sxs-lookup"><span data-stu-id="71549-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="71549-105">Není dostatek můžete jednoduše uložit změny do základní formulář.</span><span class="sxs-lookup"><span data-stu-id="71549-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="71549-106">Pokud chcete vytvořit projekt, vyberte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="71549-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71549-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="71549-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="71549-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="71549-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="71549-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="71549-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
 <span data-ttu-id="71549-110">Změny provedené v době běhu základní formulář mít žádný vliv na zděděné formuláře, které jsou již vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="71549-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71549-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="71549-111">See Also</span></span>  
 [<span data-ttu-id="71549-112">základní</span><span class="sxs-lookup"><span data-stu-id="71549-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="71549-113">Postupy: dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="71549-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [<span data-ttu-id="71549-114">Vizuální dědění Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71549-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
