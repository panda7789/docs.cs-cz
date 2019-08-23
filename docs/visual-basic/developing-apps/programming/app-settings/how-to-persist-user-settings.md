---
title: 'Postupy: Zachovat uživatelská nastavení v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 0683a5c359da1c4d082f7312c1ed8f43e1c151f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968379"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="bb297-102">Postupy: Zachovat uživatelská nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb297-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="bb297-103">Můžete použít `My.Settings.Save` metodu k uchování změn nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb297-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="bb297-104">Aplikace jsou obvykle navržené tak, aby při ukončení aplikace vytrvaly změny nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb297-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="bb297-105">Důvodem je to, že ukládání nastavení může trvat v závislosti na několika faktorech, a to několik sekund.</span><span class="sxs-lookup"><span data-stu-id="bb297-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="bb297-106">Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="bb297-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb297-107">I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově.</span><span class="sxs-lookup"><span data-stu-id="bb297-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="bb297-108">Můžete změnit nastavení rozsahu aplikace při vytváření aplikace, pomocí **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="bb297-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="bb297-109">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="bb297-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb297-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb297-110">Example</span></span>  
 <span data-ttu-id="bb297-111">Tento příklad změní hodnotu `LastChanged` nastavení uživatele a uloží tuto změnu `My.Settings.Save` voláním metody.</span><span class="sxs-lookup"><span data-stu-id="bb297-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="bb297-112">Aby tento příklad fungoval, musí mít `LastChanged` vaše aplikace uživatelské nastavení typu. `Date`</span><span class="sxs-lookup"><span data-stu-id="bb297-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="bb297-113">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="bb297-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb297-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb297-114">See also</span></span>

- [<span data-ttu-id="bb297-115">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="bb297-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="bb297-116">Postupy: Číst nastavení aplikace v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb297-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="bb297-117">Postupy: Změna uživatelského nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb297-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="bb297-118">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb297-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="bb297-119">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="bb297-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
