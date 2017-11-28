---
title: "Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81a79945dfc0b1501134bc1b0197c18093a5dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="aa915-102">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa915-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="aa915-103">Můžete vytvořit mřížku vlastností pro uživatelská nastavení naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastnosti uživatelského nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa915-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa915-104">Aby tento příklad fungoval musí mít vaše aplikace nastavené uživatelské nastavení.</span><span class="sxs-lookup"><span data-stu-id="aa915-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="aa915-105">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="aa915-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="aa915-106">`My.Settings` Objekt zpřístupňuje každé nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa915-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="aa915-107">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="aa915-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="aa915-108">Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace**-oboru nastavení je jen pro čtení, při vlastnost pro **uživatele**-oboru nastavení je pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="aa915-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="aa915-109">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="aa915-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa915-110">Nejde změnit nebo uložit hodnoty nastavení aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa915-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="aa915-111">Nastavení aplikace lze změnit pouze při vytváření aplikace (pomocí **Návrhář projektu**) nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa915-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="aa915-112">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="aa915-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="aa915-113">Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem uživatelského nastavení `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa915-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="aa915-114">Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="aa915-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="aa915-115">Ale mít vlastnosti uživatelského nastavení <xref:System.Configuration.UserScopedSettingAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="aa915-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="aa915-116">Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost <xref:System.Windows.Forms.PropertyGrid> k <xref:System.Configuration.UserScopedSettingAttribute> k zobrazení pouze vlastnosti uživatelského nastavení.</span><span class="sxs-lookup"><span data-stu-id="aa915-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="aa915-117">Chcete-li přidat mřížku vlastností nastavení uživatele</span><span class="sxs-lookup"><span data-stu-id="aa915-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="aa915-118">Přidat **PropertyGrid** řídit z **sada nástrojů** na návrhovou plochu pro vaši aplikaci, předpokládá, že zde `Form1`.</span><span class="sxs-lookup"><span data-stu-id="aa915-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="aa915-119">Výchozí název ovládacího prvku mřížky vlastnost je `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="aa915-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="aa915-120">Dvakrát klikněte na plochu návrháře pro `Form1` otevřete kód pro obslužnou rutinu události načtení formuláře.</span><span class="sxs-lookup"><span data-stu-id="aa915-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="aa915-121">Nastavte `My.Settings` objektu jako vybraný objekt pro mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="aa915-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  <span data-ttu-id="aa915-122">Nakonfigurujte mřížku vlastností zobrazí pouze nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="aa915-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="aa915-123">Chcete-li zobrazit pouze nastavení oboru aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut místo <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aa915-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="aa915-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="aa915-124">Robust Programming</span></span>  
 <span data-ttu-id="aa915-125">Při vypnutí aplikace, aplikace uloží uživatelská nastavení.</span><span class="sxs-lookup"><span data-stu-id="aa915-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="aa915-126">Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metoda.</span><span class="sxs-lookup"><span data-stu-id="aa915-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="aa915-127">Další informace najdete v tématu [postupy: zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="aa915-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa915-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa915-128">See Also</span></span>  
 [<span data-ttu-id="aa915-129">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="aa915-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="aa915-130">Postupy: čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa915-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="aa915-131">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa915-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="aa915-132">Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa915-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="aa915-133">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="aa915-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
