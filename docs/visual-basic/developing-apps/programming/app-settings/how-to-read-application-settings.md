---
title: 'Postupy: Čtení nastavení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329573"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="23327-102">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23327-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="23327-103">Můžete číst nastavení uživatele přístupem k vlastnosti nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="23327-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="23327-104">`My.Settings` Objekt zpřístupňuje každé nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="23327-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="23327-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="23327-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="23327-106">**Obor** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace** je jen pro čtení, zatímco vlastnost pro nastavení oboru **uživatele** je určena pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="23327-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="23327-107">Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="23327-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23327-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="23327-108">Example</span></span>  

 <span data-ttu-id="23327-109">V tomto příkladu se zobrazí hodnota `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="23327-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="23327-110">Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` nastavení typu. `String`</span><span class="sxs-lookup"><span data-stu-id="23327-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="23327-111">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="23327-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23327-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="23327-112">See also</span></span>

- [<span data-ttu-id="23327-113">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="23327-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="23327-114">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23327-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="23327-115">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23327-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="23327-116">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23327-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="23327-117">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="23327-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
