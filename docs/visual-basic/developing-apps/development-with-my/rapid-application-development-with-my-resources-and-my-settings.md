---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 4150d2f9634045351cb52e02c4f4807e55d118e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717891"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="e49bd-102">Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e49bd-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="e49bd-103">`My.Resources` Objekt poskytuje přístup k prostředkům vaší aplikace a vám umožní dynamicky načíst prostředky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e49bd-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="e49bd-104">Načítání prostředků</span><span class="sxs-lookup"><span data-stu-id="e49bd-104">Retrieving Resources</span></span>  
 <span data-ttu-id="e49bd-105">Počet prostředků, jako jsou zvukové soubory, ikony, obrázky a řetězce lze získat pomocí `My.Resources` objektu.</span><span class="sxs-lookup"><span data-stu-id="e49bd-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="e49bd-106">Například můžete přistupovat soubory prostředků specifické pro jazykovou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="e49bd-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="e49bd-107">Následující příklad nastaví ikony ve formuláři na ikonu s názvem `Form1Icon` uložené v souboru prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="e49bd-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="e49bd-108">`My.Resources` Zpřístupňuje pouze globální prostředky.</span><span class="sxs-lookup"><span data-stu-id="e49bd-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="e49bd-109">Neposkytuje přístup k prostředku soubory spojené s formuláři.</span><span class="sxs-lookup"><span data-stu-id="e49bd-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="e49bd-110">Musí přístup k prostředkům formuláře z formuláře.</span><span class="sxs-lookup"><span data-stu-id="e49bd-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="e49bd-111">Podobně platí `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e49bd-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="e49bd-112">Další informace najdete v tématu [My.resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e49bd-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49bd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e49bd-113">See also</span></span>
- [<span data-ttu-id="e49bd-114">Objekt My.Resources</span><span class="sxs-lookup"><span data-stu-id="e49bd-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="e49bd-115">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="e49bd-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="e49bd-116">Přístup k nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="e49bd-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/index.md)
