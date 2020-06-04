---
title: 'Postupy: Zachování uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410150"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="d448f-102">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d448f-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="d448f-103">Můžete použít `My.Settings.Save` metodu k uchování změn nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="d448f-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="d448f-104">Aplikace jsou obvykle navržené tak, aby při ukončení aplikace vytrvaly změny nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="d448f-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="d448f-105">Důvodem je to, že ukládání nastavení může trvat v závislosti na několika faktorech, a to několik sekund.</span><span class="sxs-lookup"><span data-stu-id="d448f-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="d448f-106">Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="d448f-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d448f-107">I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově.</span><span class="sxs-lookup"><span data-stu-id="d448f-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="d448f-108">Můžete změnit nastavení rozsahu aplikace při vytváření aplikace, pomocí **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d448f-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="d448f-109">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d448f-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d448f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d448f-110">Example</span></span>  

 <span data-ttu-id="d448f-111">Tento příklad změní hodnotu `LastChanged` nastavení uživatele a uloží tuto změnu voláním `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="d448f-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="d448f-112">Aby tento příklad fungoval, musí mít vaše aplikace `LastChanged` uživatelské nastavení typu `Date` .</span><span class="sxs-lookup"><span data-stu-id="d448f-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="d448f-113">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d448f-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d448f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d448f-114">See also</span></span>

- [<span data-ttu-id="d448f-115">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="d448f-115">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="d448f-116">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d448f-116">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="d448f-117">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d448f-117">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="d448f-118">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d448f-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="d448f-119">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="d448f-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
