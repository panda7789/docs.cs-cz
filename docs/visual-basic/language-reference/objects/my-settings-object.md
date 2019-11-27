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
# <a name="mysettings-object"></a><span data-ttu-id="c4956-102">My.Settings – objekt</span><span class="sxs-lookup"><span data-stu-id="c4956-102">My.Settings Object</span></span>
<span data-ttu-id="c4956-103">Poskytuje vlastnosti a metody pro přístup k nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4956-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4956-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4956-104">Remarks</span></span>  
 <span data-ttu-id="c4956-105">Objekt `My.Settings` poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c4956-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="c4956-106">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c4956-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c4956-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c4956-107">Properties</span></span>  
 <span data-ttu-id="c4956-108">Vlastnosti objektu `My.Settings` poskytují přístup k nastavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4956-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="c4956-109">Chcete-li přidat nebo odebrat nastavení, použijte **Návrháře nastavení**.</span><span class="sxs-lookup"><span data-stu-id="c4956-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="c4956-110">Každé nastavení má **název**, **typ**, **Rozsah**a **hodnotu**a tato nastavení určují, jak se vlastnost pro přístup jednotlivých nastavení zobrazí v objektu `My.Settings`:</span><span class="sxs-lookup"><span data-stu-id="c4956-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="c4956-111">**Název** Určuje název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4956-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="c4956-112">**Typ** určuje typ vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4956-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="c4956-113">**Scope** určuje, zda je vlastnost určena pouze pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c4956-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="c4956-114">Pokud je hodnota **aplikace**, vlastnost je jen pro čtení; Pokud je hodnota **uživatel**, vlastnost je určena pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="c4956-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="c4956-115">**Hodnota** je výchozí hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4956-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4956-116">Metody</span><span class="sxs-lookup"><span data-stu-id="c4956-116">Methods</span></span>  
  
|<span data-ttu-id="c4956-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4956-117">Method</span></span>|<span data-ttu-id="c4956-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c4956-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="c4956-119">Znovu načte uživatelská nastavení z naposledy uložených hodnot.</span><span class="sxs-lookup"><span data-stu-id="c4956-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="c4956-120">Uloží aktuální nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="c4956-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="c4956-121">Objekt `My.Settings` také poskytuje pokročilé vlastnosti a metody děděné z třídy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="c4956-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c4956-122">Úlohy</span><span class="sxs-lookup"><span data-stu-id="c4956-122">Tasks</span></span>  
 <span data-ttu-id="c4956-123">V následující tabulce jsou uvedeny příklady úloh týkajících se `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="c4956-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="c4956-124">Do</span><span class="sxs-lookup"><span data-stu-id="c4956-124">To</span></span>|<span data-ttu-id="c4956-125">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="c4956-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="c4956-126">Čtení nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="c4956-126">Read an application setting</span></span>|[<span data-ttu-id="c4956-127">Postupy: čtení nastavení aplikace v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="c4956-128">Změna uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="c4956-128">Change a user setting</span></span>|[<span data-ttu-id="c4956-129">Postupy: Změna uživatelského nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="c4956-130">Zachovat uživatelská nastavení</span><span class="sxs-lookup"><span data-stu-id="c4956-130">Persist user settings</span></span>|[<span data-ttu-id="c4956-131">Postupy: zachování uživatelských nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="c4956-132">Vytvořit mřížku vlastností pro uživatelská nastavení</span><span class="sxs-lookup"><span data-stu-id="c4956-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="c4956-133">Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="c4956-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4956-134">Example</span></span>  
 <span data-ttu-id="c4956-135">V tomto příkladu se zobrazí hodnota nastavení `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="c4956-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="c4956-136">Aby tento příklad fungoval, musí mít aplikace `Nickname` nastavení typu `String`.</span><span class="sxs-lookup"><span data-stu-id="c4956-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4956-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4956-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="c4956-138">Postupy: čtení nastavení aplikace v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="c4956-139">Postupy: Změna uživatelského nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="c4956-140">Postupy: zachování uživatelských nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="c4956-141">Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4956-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="c4956-142">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="c4956-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
