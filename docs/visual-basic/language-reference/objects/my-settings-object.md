---
title: My.Settings – objekt
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: c905ff85c8e9729dd4d6068f0d34f729962bbb57
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372398"
---
# <a name="mysettings-object"></a><span data-ttu-id="3b09b-102">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="3b09b-102">My.Settings Object</span></span>
<span data-ttu-id="3b09b-103">Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b09b-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b09b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b09b-104">Remarks</span></span>  
 <span data-ttu-id="3b09b-105">`My.Settings`Objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b09b-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="3b09b-106">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="3b09b-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b09b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3b09b-107">Properties</span></span>  
 <span data-ttu-id="3b09b-108">Vlastnosti `My.Settings` objektu poskytují přístup k nastavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b09b-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="3b09b-109">Chcete-li přidat nebo odebrat nastavení, použijte **Návrháře nastavení**.</span><span class="sxs-lookup"><span data-stu-id="3b09b-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="3b09b-110">Každé nastavení má **název**, **typ**, **Rozsah**a **hodnotu**a tato nastavení určují, jak se vlastnost pro přístup jednotlivých nastavení zobrazí v `My.Settings` objektu:</span><span class="sxs-lookup"><span data-stu-id="3b09b-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="3b09b-111">**Název** Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3b09b-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="3b09b-112">**Typ** určuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3b09b-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="3b09b-113">**Scope** určuje, zda je vlastnost určena pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="3b09b-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="3b09b-114">Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatel**, vlastnost je určena pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="3b09b-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="3b09b-115">**Hodnota** je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3b09b-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b09b-116">Metody</span><span class="sxs-lookup"><span data-stu-id="3b09b-116">Methods</span></span>  
  
|<span data-ttu-id="3b09b-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b09b-117">Method</span></span>|<span data-ttu-id="3b09b-118">Description</span><span class="sxs-lookup"><span data-stu-id="3b09b-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="3b09b-119">Znovu načte uživatelská nastavení z naposledy uložených hodnot.</span><span class="sxs-lookup"><span data-stu-id="3b09b-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="3b09b-120">Uloží aktuální nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="3b09b-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="3b09b-121">`My.Settings`Objekt také poskytuje pokročilé vlastnosti a metody děděné z <xref:System.Configuration.ApplicationSettingsBase> třídy.</span><span class="sxs-lookup"><span data-stu-id="3b09b-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3b09b-122">Úlohy</span><span class="sxs-lookup"><span data-stu-id="3b09b-122">Tasks</span></span>  
 <span data-ttu-id="3b09b-123">V následující tabulce jsou uvedeny příklady úloh týkajících se `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="3b09b-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="3b09b-124">Akce</span><span class="sxs-lookup"><span data-stu-id="3b09b-124">To</span></span>|<span data-ttu-id="3b09b-125">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="3b09b-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="3b09b-126">Čtení nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="3b09b-126">Read an application setting</span></span>|[<span data-ttu-id="3b09b-127">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-127">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="3b09b-128">Změna uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="3b09b-128">Change a user setting</span></span>|[<span data-ttu-id="3b09b-129">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-129">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="3b09b-130">Zachovat uživatelská nastavení</span><span class="sxs-lookup"><span data-stu-id="3b09b-130">Persist user settings</span></span>|[<span data-ttu-id="3b09b-131">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-131">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="3b09b-132">Vytvořit mřížku vlastností pro uživatelská nastavení</span><span class="sxs-lookup"><span data-stu-id="3b09b-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="3b09b-133">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="3b09b-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b09b-134">Example</span></span>  
 <span data-ttu-id="3b09b-135">V tomto příkladu se zobrazí hodnota `Nickname` nastavení.</span><span class="sxs-lookup"><span data-stu-id="3b09b-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="3b09b-136">Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` Nastavení typu `String` .</span><span class="sxs-lookup"><span data-stu-id="3b09b-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b09b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b09b-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="3b09b-138">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-138">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="3b09b-139">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-139">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="3b09b-140">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-140">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="3b09b-141">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b09b-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="3b09b-142">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="3b09b-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
