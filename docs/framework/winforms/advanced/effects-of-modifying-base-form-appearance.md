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
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040132"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="de6e4-102">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="de6e4-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="de6e4-103">Během vývoje aplikace může být často nutné změnit vzhled základního formuláře, ze kterého jsou děděny jiné formuláře v projektu (nebo v jiných projektech).</span><span class="sxs-lookup"><span data-stu-id="de6e4-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="de6e4-104">V době návrhu se změny ve vzhledu základního formuláře projeví ve zděděných formulářích, pokud je projekt obsahující základní formulář sestavený jako první.</span><span class="sxs-lookup"><span data-stu-id="de6e4-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="de6e4-105">Nestačí, když budete změny jednoduše ukládat do základního formuláře.</span><span class="sxs-lookup"><span data-stu-id="de6e4-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="de6e4-106">Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **sestavit** .</span><span class="sxs-lookup"><span data-stu-id="de6e4-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="de6e4-107">Změny provedené v základním formuláři za běhu nemají vliv na zděděné formuláře, které již jsou vytvořeny instance.</span><span class="sxs-lookup"><span data-stu-id="de6e4-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="de6e4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de6e4-108">See also</span></span>

- [<span data-ttu-id="de6e4-109">base</span><span class="sxs-lookup"><span data-stu-id="de6e4-109">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="de6e4-110">Postupy: Zdědit model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de6e4-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="de6e4-111">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de6e4-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
