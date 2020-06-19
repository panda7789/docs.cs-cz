---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990206"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="82f00-102">Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82f00-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="82f00-103">`My.Resources`Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načítat prostředky pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82f00-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="82f00-104">Načítání prostředků</span><span class="sxs-lookup"><span data-stu-id="82f00-104">Retrieving Resources</span></span>  

 <span data-ttu-id="82f00-105">Pomocí objektu lze načíst řadu prostředků, jako jsou například zvukové soubory, ikony, obrázky a řetězce `My.Resources` .</span><span class="sxs-lookup"><span data-stu-id="82f00-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="82f00-106">Můžete například získat přístup k souborům prostředků specifických pro jazykovou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="82f00-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="82f00-107">Následující příklad nastaví ikonu formuláře na ikonu s názvem `Form1Icon` uloženou v souboru prostředků aplikace.</span><span class="sxs-lookup"><span data-stu-id="82f00-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="82f00-108">`My.Resources`Objekt zpřístupňuje pouze globální prostředky.</span><span class="sxs-lookup"><span data-stu-id="82f00-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="82f00-109">Neposkytuje přístup k souborům prostředků přidruženým k formulářům.</span><span class="sxs-lookup"><span data-stu-id="82f00-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="82f00-110">Přístup k prostředkům formuláře z formuláře.</span><span class="sxs-lookup"><span data-stu-id="82f00-110">Access the form resources from the form.</span></span>  
  
 <span data-ttu-id="82f00-111">Podobně `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82f00-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="82f00-112">Další informace naleznete v tématu [objekt My. Resources](../../language-reference/objects/my-resources-object.md) a [My. Settings Object](../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="82f00-112">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f00-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="82f00-113">See also</span></span>

- [<span data-ttu-id="82f00-114">My.Resources – objekt</span><span class="sxs-lookup"><span data-stu-id="82f00-114">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="82f00-115">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="82f00-115">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="82f00-116">Přístup k nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="82f00-116">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
