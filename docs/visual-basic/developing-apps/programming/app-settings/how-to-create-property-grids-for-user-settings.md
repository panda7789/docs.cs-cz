---
title: 'How to: Create Property Grids for User Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: bed4e8a2b50f0115c3b8d9d6abf427df5f216388
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329615"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="f715b-102">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f715b-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="f715b-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="f715b-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f715b-104">In order for this example to work, your application must have its user settings configured.</span><span class="sxs-lookup"><span data-stu-id="f715b-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="f715b-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f715b-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f715b-106">The `My.Settings` object exposes each setting as a property.</span><span class="sxs-lookup"><span data-stu-id="f715b-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="f715b-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span><span class="sxs-lookup"><span data-stu-id="f715b-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="f715b-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span><span class="sxs-lookup"><span data-stu-id="f715b-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="f715b-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f715b-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f715b-110">You cannot change or save the values of application-scope settings at run time.</span><span class="sxs-lookup"><span data-stu-id="f715b-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="f715b-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="f715b-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="f715b-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f715b-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="f715b-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="f715b-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="f715b-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="f715b-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="f715b-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span><span class="sxs-lookup"><span data-stu-id="f715b-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="f715b-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span><span class="sxs-lookup"><span data-stu-id="f715b-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="f715b-117">To add a user setting property grid</span><span class="sxs-lookup"><span data-stu-id="f715b-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="f715b-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f715b-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="f715b-119">The default name of the property-grid control is `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="f715b-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="f715b-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span><span class="sxs-lookup"><span data-stu-id="f715b-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="f715b-121">Set the `My.Settings` object as the selected object for the property grid.</span><span class="sxs-lookup"><span data-stu-id="f715b-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="f715b-122">Configure the property grid to show only the user settings.</span><span class="sxs-lookup"><span data-stu-id="f715b-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="f715b-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f715b-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f715b-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f715b-124">Robust Programming</span></span>  

 <span data-ttu-id="f715b-125">The application saves the user settings when the application shuts down.</span><span class="sxs-lookup"><span data-stu-id="f715b-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="f715b-126">To save the settings immediately, call the `My.Settings.Save` method.</span><span class="sxs-lookup"><span data-stu-id="f715b-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="f715b-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f715b-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f715b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f715b-128">See also</span></span>

- [<span data-ttu-id="f715b-129">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="f715b-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="f715b-130">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f715b-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="f715b-131">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f715b-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="f715b-132">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f715b-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="f715b-133">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="f715b-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
