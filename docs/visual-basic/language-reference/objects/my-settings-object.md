---
title: My.Settings – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 54176ae6706311b17227c7dc21a5060c9b369753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603029"
---
# <a name="mysettings-object"></a><span data-ttu-id="1dfdd-102">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="1dfdd-102">My.Settings Object</span></span>
<span data-ttu-id="1dfdd-103">Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dfdd-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1dfdd-104">Remarks</span></span>  
 <span data-ttu-id="1dfdd-105">`My.Settings` Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládání a načítání nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="1dfdd-106">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="1dfdd-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1dfdd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1dfdd-107">Properties</span></span>  
 <span data-ttu-id="1dfdd-108">Vlastnosti `My.Settings` objekt poskytnout přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="1dfdd-109">Chcete-li přidat nebo odebrat nastavení, použijte **nastavení návrháře**.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="1dfdd-110">Každé nastavení má **název**, **typ**, **oboru**, a **hodnotu**, a tato nastavení určují, jak vlastnost, která má přístup každý nastavení Zobrazí se v `My.Settings` objektu:</span><span class="sxs-lookup"><span data-stu-id="1dfdd-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
-   <span data-ttu-id="1dfdd-111">**Název** Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-111">**Name** determines the name of the property.</span></span>  
  
-   <span data-ttu-id="1dfdd-112">**Typ** Určuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-112">**Type** determines the type of the property.</span></span>  
  
-   <span data-ttu-id="1dfdd-113">**Obor** označuje, zda je vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="1dfdd-114">Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatele**, vlastnost je pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
-   <span data-ttu-id="1dfdd-115">**Hodnota** je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dfdd-116">Metody</span><span class="sxs-lookup"><span data-stu-id="1dfdd-116">Methods</span></span>  
  
|<span data-ttu-id="1dfdd-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="1dfdd-117">Method</span></span>|<span data-ttu-id="1dfdd-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1dfdd-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="1dfdd-119">Znovu načte nastavení uživatele z poslední uložené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="1dfdd-120">Uloží aktuální nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="1dfdd-121">`My.Settings` Objekt také poskytuje rozšířené vlastnosti a metody, dědí z <xref:System.Configuration.ApplicationSettingsBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="1dfdd-122">Úlohy</span><span class="sxs-lookup"><span data-stu-id="1dfdd-122">Tasks</span></span>  
 <span data-ttu-id="1dfdd-123">V následující tabulce jsou uvedeny příklady úkolů zahrnující `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="1dfdd-124">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="1dfdd-124">To</span></span>|<span data-ttu-id="1dfdd-125">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="1dfdd-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="1dfdd-126">Čtení nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="1dfdd-126">Read an application setting</span></span>|[<span data-ttu-id="1dfdd-127">Postupy: čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="1dfdd-128">Změňte uživatelské nastavení</span><span class="sxs-lookup"><span data-stu-id="1dfdd-128">Change a user setting</span></span>|[<span data-ttu-id="1dfdd-129">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="1dfdd-130">Zachování uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="1dfdd-130">Persist user settings</span></span>|[<span data-ttu-id="1dfdd-131">Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="1dfdd-132">Vytvořit mřížku vlastností pro nastavení uživatele</span><span class="sxs-lookup"><span data-stu-id="1dfdd-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="1dfdd-133">Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="1dfdd-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="1dfdd-134">Example</span></span>  
 <span data-ttu-id="1dfdd-135">Tento příklad zobrazuje hodnotu `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 <span data-ttu-id="1dfdd-136">Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.</span><span class="sxs-lookup"><span data-stu-id="1dfdd-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dfdd-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dfdd-137">See Also</span></span>  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [<span data-ttu-id="1dfdd-138">Postupy: čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [<span data-ttu-id="1dfdd-139">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [<span data-ttu-id="1dfdd-140">Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [<span data-ttu-id="1dfdd-141">Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfdd-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [<span data-ttu-id="1dfdd-142">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="1dfdd-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
