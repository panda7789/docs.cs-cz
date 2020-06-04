---
title: 'Postupy: Čtení nastavení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410137"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="8322b-102">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8322b-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="8322b-103">Můžete číst nastavení uživatele přístupem k vlastnosti nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="8322b-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="8322b-104">`My.Settings`Objekt zpřístupňuje každé nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8322b-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="8322b-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="8322b-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="8322b-106">**Obor** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace** je jen pro čtení, zatímco vlastnost pro nastavení oboru **uživatele** je určena pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="8322b-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="8322b-107">Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="8322b-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8322b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8322b-108">Example</span></span>  

 <span data-ttu-id="8322b-109">V tomto příkladu se zobrazí hodnota `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="8322b-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="8322b-110">Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` Nastavení typu `String` .</span><span class="sxs-lookup"><span data-stu-id="8322b-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="8322b-111">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="8322b-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8322b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8322b-112">See also</span></span>

- [<span data-ttu-id="8322b-113">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="8322b-113">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="8322b-114">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8322b-114">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="8322b-115">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8322b-115">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="8322b-116">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8322b-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="8322b-117">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="8322b-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
