---
title: "Postupy: Čtení nastavení aplikace v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="7d35b-102">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d35b-102">How to: Read Application Settings in Visual Basic</span></span>
<span data-ttu-id="7d35b-103">Uživatelské nastavení si můžete přečíst v přístupu k vlastnosti nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="7d35b-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="7d35b-104">`My.Settings` Objekt zpřístupňuje každé nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d35b-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="7d35b-105">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="7d35b-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="7d35b-106">Toto nastavení **oboru** označuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace** oboru nastavení je jen pro čtení, při vlastnost pro **uživatele** obor nastavení je pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="7d35b-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="7d35b-107">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="7d35b-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d35b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d35b-108">Example</span></span>  
 <span data-ttu-id="7d35b-109">Tento příklad zobrazuje hodnotu `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="7d35b-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 <span data-ttu-id="7d35b-110">Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.</span><span class="sxs-lookup"><span data-stu-id="7d35b-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="7d35b-111">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="7d35b-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d35b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d35b-112">See Also</span></span>  
 [<span data-ttu-id="7d35b-113">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="7d35b-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="7d35b-114">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d35b-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="7d35b-115">Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d35b-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="7d35b-116">Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d35b-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="7d35b-117">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="7d35b-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
