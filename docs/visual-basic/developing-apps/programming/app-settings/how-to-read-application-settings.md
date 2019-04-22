---
title: 'Postupy: Čtení nastavení aplikace v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823581"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="05f35-102">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05f35-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="05f35-103">Nastavením hlavního názvu uživatele si můžete přečíst na přístupem k nastavení vlastnosti `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="05f35-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="05f35-104">`My.Settings` Objekt poskytuje každému nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="05f35-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="05f35-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typů nastavení.</span><span class="sxs-lookup"><span data-stu-id="05f35-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="05f35-106">Toto nastavení **oboru** značí, zda je vlastnost jen pro čtení; vlastnost pro **aplikace** nastavení oboru je jen pro čtení, při vlastnost pro **uživatele** obor nastavení je pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="05f35-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="05f35-107">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="05f35-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05f35-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="05f35-108">Example</span></span>  
 <span data-ttu-id="05f35-109">Tento příklad zobrazuje hodnotu `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="05f35-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="05f35-110">Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.</span><span class="sxs-lookup"><span data-stu-id="05f35-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="05f35-111">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="05f35-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f35-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05f35-112">See also</span></span>

- [<span data-ttu-id="05f35-113">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="05f35-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="05f35-114">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05f35-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="05f35-115">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05f35-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="05f35-116">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05f35-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="05f35-117">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="05f35-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
