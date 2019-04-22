---
title: 'Postupy: Zachování uživatelského nastavení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 35997db52a59aeaff5a2c404ea83b15639ea23a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825178"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="7a6b4-102">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a6b4-102">How to: Persist User Settings in Visual Basic</span></span>
<span data-ttu-id="7a6b4-103">Můžete použít `My.Settings.Save` metoda zachování změn nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="7a6b4-104">Aplikace jsou obvykle určeny a zachová tak změny nastavení pro uživatele po vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="7a6b4-105">Důvodem je skutečnost ukládá se nastavení lze provést, v závislosti na několika faktorech, několik sekund.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="7a6b4-106">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="7a6b4-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a6b4-107">I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele za běhu, nastavení oboru aplikace jsou jen pro čtení a nedá se změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="7a6b4-108">Při vytváření aplikace, prostřednictvím můžete změnit nastavení oboru aplikace **Návrháře projektu**, nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="7a6b4-109">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7a6b4-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a6b4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a6b4-110">Example</span></span>  
 <span data-ttu-id="7a6b4-111">V tomto příkladu změní hodnotu `LastChanged` nastavení hlavního názvu uživatele a uloží změny voláním `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="7a6b4-112">Pro tento příklad fungoval, musí mít vaše aplikace `LastChanged` nastavení hlavního názvu uživatele, typu `Date`.</span><span class="sxs-lookup"><span data-stu-id="7a6b4-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="7a6b4-113">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7a6b4-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6b4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a6b4-114">See also</span></span>

- [<span data-ttu-id="7a6b4-115">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="7a6b4-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="7a6b4-116">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a6b4-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="7a6b4-117">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a6b4-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="7a6b4-118">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a6b4-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="7a6b4-119">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="7a6b4-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
