---
title: My.Settings – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350362"
---
# <a name="mysettings-object"></a><span data-ttu-id="6127e-102">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="6127e-102">My.Settings Object</span></span>
<span data-ttu-id="6127e-103">Provides properties and methods for accessing the application's settings.</span><span class="sxs-lookup"><span data-stu-id="6127e-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6127e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6127e-104">Remarks</span></span>  
 <span data-ttu-id="6127e-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span><span class="sxs-lookup"><span data-stu-id="6127e-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="6127e-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6127e-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6127e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6127e-107">Properties</span></span>  
 <span data-ttu-id="6127e-108">The properties of the `My.Settings` object provide access to your application's settings.</span><span class="sxs-lookup"><span data-stu-id="6127e-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="6127e-109">To add or remove settings, use the **Settings Designer**.</span><span class="sxs-lookup"><span data-stu-id="6127e-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="6127e-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span><span class="sxs-lookup"><span data-stu-id="6127e-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="6127e-111">**Name** determines the name of the property.</span><span class="sxs-lookup"><span data-stu-id="6127e-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="6127e-112">**Type** determines the type of the property.</span><span class="sxs-lookup"><span data-stu-id="6127e-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="6127e-113">**Scope** indicates if the property is read-only.</span><span class="sxs-lookup"><span data-stu-id="6127e-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="6127e-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span><span class="sxs-lookup"><span data-stu-id="6127e-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="6127e-115">**Value** is the default value of the property.</span><span class="sxs-lookup"><span data-stu-id="6127e-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6127e-116">Metody</span><span class="sxs-lookup"><span data-stu-id="6127e-116">Methods</span></span>  
  
|<span data-ttu-id="6127e-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="6127e-117">Method</span></span>|<span data-ttu-id="6127e-118">Popis</span><span class="sxs-lookup"><span data-stu-id="6127e-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="6127e-119">Reloads the user settings from the last saved values.</span><span class="sxs-lookup"><span data-stu-id="6127e-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="6127e-120">Saves the current user settings.</span><span class="sxs-lookup"><span data-stu-id="6127e-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="6127e-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span><span class="sxs-lookup"><span data-stu-id="6127e-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="6127e-122">Úkoly</span><span class="sxs-lookup"><span data-stu-id="6127e-122">Tasks</span></span>  
 <span data-ttu-id="6127e-123">The following table lists examples of tasks involving the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="6127e-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="6127e-124">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="6127e-124">To</span></span>|<span data-ttu-id="6127e-125">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="6127e-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="6127e-126">Read an application setting</span><span class="sxs-lookup"><span data-stu-id="6127e-126">Read an application setting</span></span>|[<span data-ttu-id="6127e-127">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="6127e-128">Change a user setting</span><span class="sxs-lookup"><span data-stu-id="6127e-128">Change a user setting</span></span>|[<span data-ttu-id="6127e-129">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="6127e-130">Persist user settings</span><span class="sxs-lookup"><span data-stu-id="6127e-130">Persist user settings</span></span>|[<span data-ttu-id="6127e-131">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="6127e-132">Create a property grid for user settings</span><span class="sxs-lookup"><span data-stu-id="6127e-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="6127e-133">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="6127e-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="6127e-134">Example</span></span>  
 <span data-ttu-id="6127e-135">This example displays the value of the `Nickname` setting.</span><span class="sxs-lookup"><span data-stu-id="6127e-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="6127e-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span><span class="sxs-lookup"><span data-stu-id="6127e-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6127e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6127e-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="6127e-138">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="6127e-139">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="6127e-140">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="6127e-141">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6127e-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="6127e-142">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="6127e-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
