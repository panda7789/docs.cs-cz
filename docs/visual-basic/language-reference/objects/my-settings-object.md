---
title: My.Settings – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: a962f7cce961b1ee6829702a6815ba02c534efb4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050308"
---
# <a name="mysettings-object"></a><span data-ttu-id="af16c-102">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="af16c-102">My.Settings Object</span></span>
<span data-ttu-id="af16c-103">Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="af16c-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af16c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af16c-104">Remarks</span></span>  
 <span data-ttu-id="af16c-105">`My.Settings` Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af16c-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="af16c-106">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="af16c-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af16c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="af16c-107">Properties</span></span>  
 <span data-ttu-id="af16c-108">Vlastnosti `My.Settings` objekt poskytnout přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="af16c-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="af16c-109">Chcete-li přidat nebo odebrat nastavení, použijte **návrháře nastavení**.</span><span class="sxs-lookup"><span data-stu-id="af16c-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="af16c-110">Každé nastavení má **název**, **typ**, **oboru**, a **hodnota**, a tato nastavení určují, jak vlastnost, která má přístup ke každé nastavení Zobrazí se v `My.Settings` objektu:</span><span class="sxs-lookup"><span data-stu-id="af16c-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="af16c-111">**Název** Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af16c-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="af16c-112">**Typ** Určuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af16c-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="af16c-113">**Obor** značí, zda je vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="af16c-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="af16c-114">Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatele**, je vlastnost pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="af16c-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="af16c-115">**Hodnota** je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af16c-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af16c-116">Metody</span><span class="sxs-lookup"><span data-stu-id="af16c-116">Methods</span></span>  
  
|<span data-ttu-id="af16c-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="af16c-117">Method</span></span>|<span data-ttu-id="af16c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="af16c-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="af16c-119">Znovu načte nastavení uživatele z poslední uložené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="af16c-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="af16c-120">Uloží aktuální nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="af16c-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="af16c-121">`My.Settings` Objekt poskytuje také pokročilé vlastností a metod zděděných z <xref:System.Configuration.ApplicationSettingsBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="af16c-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="af16c-122">Úkoly</span><span class="sxs-lookup"><span data-stu-id="af16c-122">Tasks</span></span>  
 <span data-ttu-id="af16c-123">Následující tabulka uvádí příklady úloh týkajících `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="af16c-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="af16c-124">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="af16c-124">To</span></span>|<span data-ttu-id="af16c-125">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="af16c-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="af16c-126">Čtení nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="af16c-126">Read an application setting</span></span>|[<span data-ttu-id="af16c-127">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="af16c-128">Změna uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="af16c-128">Change a user setting</span></span>|[<span data-ttu-id="af16c-129">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="af16c-130">Zachování uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="af16c-130">Persist user settings</span></span>|[<span data-ttu-id="af16c-131">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="af16c-132">Vytvořit mřížku vlastností pro uživatelská nastavení</span><span class="sxs-lookup"><span data-stu-id="af16c-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="af16c-133">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="af16c-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="af16c-134">Example</span></span>  
 <span data-ttu-id="af16c-135">Tento příklad zobrazuje hodnotu `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="af16c-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="af16c-136">Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`.</span><span class="sxs-lookup"><span data-stu-id="af16c-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af16c-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af16c-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="af16c-138">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="af16c-139">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="af16c-140">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="af16c-141">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af16c-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="af16c-142">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="af16c-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
