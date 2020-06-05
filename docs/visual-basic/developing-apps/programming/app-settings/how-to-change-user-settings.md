---
title: 'Postupy: Změna uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: c9b89459f9b443c3a447edce90fee3437bbf1b6a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410176"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="5e938-102">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e938-102">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="5e938-103">Nastavení uživatele můžete změnit přiřazením nové hodnoty k vlastnosti nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="5e938-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="5e938-104">`My.Settings`Objekt zpřístupňuje každé nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5e938-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="5e938-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="5e938-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="5e938-106">**Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení: vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení oboru **uživatele**je určena pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="5e938-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="5e938-107">Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5e938-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e938-108">I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově.</span><span class="sxs-lookup"><span data-stu-id="5e938-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="5e938-109">Můžete změnit nastavení rozsahu aplikace při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e938-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="5e938-110">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5e938-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e938-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e938-111">Example</span></span>  

 <span data-ttu-id="5e938-112">Tento příklad změní hodnotu `Nickname` nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="5e938-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="5e938-113">Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` uživatelské nastavení typu `String` .</span><span class="sxs-lookup"><span data-stu-id="5e938-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="5e938-114">Aplikace uloží nastavení uživatele, když se aplikace vypíná.</span><span class="sxs-lookup"><span data-stu-id="5e938-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="5e938-115">Chcete-li nastavení uložit hned, zavolejte `My.Settings.Save` metodu.</span><span class="sxs-lookup"><span data-stu-id="5e938-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="5e938-116">Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="5e938-116">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e938-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e938-117">See also</span></span>

- [<span data-ttu-id="5e938-118">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="5e938-118">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5e938-119">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e938-119">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="5e938-120">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e938-120">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="5e938-121">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e938-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="5e938-122">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="5e938-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
