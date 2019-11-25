---
title: 'How to: Persist User Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329631"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a><span data-ttu-id="f6541-102">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6541-102">How to: Persist User Settings in Visual Basic</span></span>

<span data-ttu-id="f6541-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span><span class="sxs-lookup"><span data-stu-id="f6541-103">You can use the `My.Settings.Save` method to persist changes to the user settings.</span></span>  
  
 <span data-ttu-id="f6541-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span><span class="sxs-lookup"><span data-stu-id="f6541-104">Typically, applications are designed to persist the changes to the user settings when the application shuts down.</span></span> <span data-ttu-id="f6541-105">This is because saving the settings can take, depending on several factors, several seconds.</span><span class="sxs-lookup"><span data-stu-id="f6541-105">This is because saving the settings can take, depending on several factors, several seconds.</span></span>  
  
 <span data-ttu-id="f6541-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f6541-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6541-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span><span class="sxs-lookup"><span data-stu-id="f6541-107">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="f6541-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="f6541-108">You can change application-scope settings when creating the application, through the **Project Designer**, or by editing the application's configuration file.</span></span> <span data-ttu-id="f6541-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f6541-109">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6541-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6541-110">Example</span></span>  

 <span data-ttu-id="f6541-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span><span class="sxs-lookup"><span data-stu-id="f6541-111">This example changes the value of the `LastChanged` user setting and saves that change by calling the `My.Settings.Save` method.</span></span>  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 <span data-ttu-id="f6541-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span><span class="sxs-lookup"><span data-stu-id="f6541-112">For this example to work, your application must have a `LastChanged` user setting, of type `Date`.</span></span> <span data-ttu-id="f6541-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f6541-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6541-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6541-114">See also</span></span>

- [<span data-ttu-id="f6541-115">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="f6541-115">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="f6541-116">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6541-116">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="f6541-117">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6541-117">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="f6541-118">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6541-118">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="f6541-119">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="f6541-119">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
