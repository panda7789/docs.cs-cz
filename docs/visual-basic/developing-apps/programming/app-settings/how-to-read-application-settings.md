---
title: 'How to: Read Application Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329573"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="9d1c5-102">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d1c5-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="9d1c5-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="9d1c5-104">The `My.Settings` object exposes each setting as a property.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="9d1c5-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="9d1c5-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="9d1c5-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="9d1c5-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d1c5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d1c5-108">Example</span></span>  

 <span data-ttu-id="9d1c5-109">This example displays the value of the `Nickname` setting.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="9d1c5-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span><span class="sxs-lookup"><span data-stu-id="9d1c5-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="9d1c5-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9d1c5-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1c5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d1c5-112">See also</span></span>

- [<span data-ttu-id="9d1c5-113">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="9d1c5-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="9d1c5-114">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d1c5-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="9d1c5-115">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d1c5-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="9d1c5-116">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d1c5-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="9d1c5-117">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="9d1c5-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
