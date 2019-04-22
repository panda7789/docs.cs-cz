---
title: 'Postupy: Změna uživatelského nastavení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 05c95026d061918b38cf301209afefa9498e33bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820968"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="45c71-102">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45c71-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="45c71-103">Uživatelské nastavení můžete změnit přiřazení nové hodnoty pro nastavení vlastnosti na `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="45c71-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="45c71-104">`My.Settings` Objekt poskytuje každému nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="45c71-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="45c71-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typů nastavení.</span><span class="sxs-lookup"><span data-stu-id="45c71-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="45c71-106">Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení: Vlastnost pro **aplikace**– obor nastavení je jen pro čtení, při vlastnost pro **uživatele**– obor nastavení je pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="45c71-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="45c71-107">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="45c71-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45c71-108">I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele za běhu, nastavení oboru aplikace jsou jen pro čtení a nedá se změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="45c71-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="45c71-109">Nastavení oboru aplikace můžete změnit, když vytvoříte aplikaci pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="45c71-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="45c71-110">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="45c71-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c71-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="45c71-111">Example</span></span>  
 <span data-ttu-id="45c71-112">V tomto příkladu změní hodnotu `Nickname` nastavení hlavního názvu uživatele.</span><span class="sxs-lookup"><span data-stu-id="45c71-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="45c71-113">Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` nastavení hlavního názvu uživatele, typu `String`.</span><span class="sxs-lookup"><span data-stu-id="45c71-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="45c71-114">Aplikace ukládá uživatelská nastavení při ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="45c71-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="45c71-115">Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="45c71-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="45c71-116">Další informace najdete v tématu [jak: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="45c71-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c71-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45c71-117">See also</span></span>

- [<span data-ttu-id="45c71-118">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="45c71-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="45c71-119">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45c71-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="45c71-120">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45c71-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="45c71-121">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45c71-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="45c71-122">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="45c71-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
