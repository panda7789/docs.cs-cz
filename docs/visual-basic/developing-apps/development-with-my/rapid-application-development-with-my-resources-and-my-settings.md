---
title: "Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="ce7e4-102">Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce7e4-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="ce7e4-103">`My.Resources` Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načíst prostředky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="ce7e4-104">Načítání prostředků</span><span class="sxs-lookup"><span data-stu-id="ce7e4-104">Retrieving Resources</span></span>  
 <span data-ttu-id="ce7e4-105">Počet prostředků, jako je například zvukové soubory, ikony, Image a řetězce mohou být načteny prostřednictvím `My.Resources` objektu.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="ce7e4-106">Například můžete přístup k souborům prostředků specifické pro jazykovou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="ce7e4-107">Následující příklad nastaví ikona formuláře na ikonu s názvem `Form1Icon` uložené v souboru prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="ce7e4-108">`My.Resources` Objekt se poskytuje pouze globální prostředky.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="ce7e4-109">Neposkytuje přístup k prostředku soubory spojené s formuláři.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="ce7e4-110">Ve formuláři musí přístup k prostředkům formuláře.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-110">You must access the form resources from the form.</span></span> <span data-ttu-id="ce7e4-111">Další informace najdete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span><span class="sxs-lookup"><span data-stu-id="ce7e4-111">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="ce7e4-112">Podobně `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládání a načítání nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce7e4-112">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="ce7e4-113">Další informace najdete v tématu [My.Resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="ce7e4-113">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce7e4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce7e4-114">See Also</span></span>  
 [<span data-ttu-id="ce7e4-115">My.Resources – objekt</span><span class="sxs-lookup"><span data-stu-id="ce7e4-115">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="ce7e4-116">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="ce7e4-116">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="ce7e4-117">Přístup k nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="ce7e4-117">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
