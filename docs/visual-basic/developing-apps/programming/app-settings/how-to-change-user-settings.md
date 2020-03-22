---
title: 'Postupy: Změna uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329619"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="43264-102">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43264-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="43264-103">Nastavení uživatele můžete změnit přiřazením nové hodnoty vlastnosti nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="43264-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="43264-104">Objekt `My.Settings` zveřejňuje každé nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="43264-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="43264-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="43264-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="43264-106">**Obor** nastavení určuje, zda je vlastnost jen pro čtení: Vlastnost pro nastavení **Application**-scope je jen pro čtení, zatímco vlastnost pro nastavení **User**-scope je čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="43264-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="43264-107">Další informace naleznete v tématu [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="43264-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43264-108">Přestože můžete změnit a uložit hodnoty nastavení uživatelského oboru za běhu, nastavení oboru aplikace jsou jen pro čtení a nelze je programově změnit.</span><span class="sxs-lookup"><span data-stu-id="43264-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="43264-109">Nastavení oboru aplikace můžete změnit při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="43264-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="43264-110">Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="43264-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43264-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="43264-111">Example</span></span>  

 <span data-ttu-id="43264-112">Tento příklad změní hodnotu nastavení `Nickname` uživatele.</span><span class="sxs-lookup"><span data-stu-id="43264-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="43264-113">Aby tento příklad fungoval, musí `Nickname` mít aplikace uživatelské `String`nastavení typu .</span><span class="sxs-lookup"><span data-stu-id="43264-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="43264-114">Aplikace uloží uživatelská nastavení při vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="43264-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="43264-115">Chcete-li nastavení uložit `My.Settings.Save` okamžitě, zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="43264-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="43264-116">Další informace naleznete v [tématu How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="43264-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43264-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="43264-117">See also</span></span>

- [<span data-ttu-id="43264-118">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="43264-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="43264-119">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43264-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="43264-120">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43264-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="43264-121">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43264-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="43264-122">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="43264-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
