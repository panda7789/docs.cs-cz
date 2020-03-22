---
title: 'Postupy: Zachování uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329631"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="20b3f-102">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20b3f-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="20b3f-103">Tuto metodu `My.Settings.Save` můžete použít k zachování změn v nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="20b3f-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="20b3f-104">Aplikace jsou obvykle navrženy tak, aby zachovat změny nastavení uživatele při vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="20b3f-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="20b3f-105">Je to proto, že uložení nastavení může trvat, v závislosti na několika faktorech, několik sekund.</span><span class="sxs-lookup"><span data-stu-id="20b3f-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="20b3f-106">Další informace naleznete v tématu [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="20b3f-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20b3f-107">Přestože můžete změnit a uložit hodnoty nastavení uživatelského oboru za běhu, nastavení oboru aplikace jsou jen pro čtení a nelze je programově změnit.</span><span class="sxs-lookup"><span data-stu-id="20b3f-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="20b3f-108">Nastavení oboru aplikace můžete změnit při vytváření aplikace, prostřednictvím **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="20b3f-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="20b3f-109">Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="20b3f-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b3f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="20b3f-110">Example</span></span>  

 <span data-ttu-id="20b3f-111">Tento příklad změní hodnotu nastavení `LastChanged` uživatele a uloží `My.Settings.Save` tuto změnu voláním metody.</span><span class="sxs-lookup"><span data-stu-id="20b3f-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="20b3f-112">Aby tento příklad fungoval, musí `LastChanged` mít aplikace uživatelské `Date`nastavení typu .</span><span class="sxs-lookup"><span data-stu-id="20b3f-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="20b3f-113">Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="20b3f-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b3f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="20b3f-114">See also</span></span>

- [<span data-ttu-id="20b3f-115">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="20b3f-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="20b3f-116">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20b3f-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="20b3f-117">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20b3f-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="20b3f-118">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20b3f-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="20b3f-119">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="20b3f-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
