---
title: 'Postupy: vytváření mřížek vlastností pro uživatelská nastavení'
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
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="d5427-102">Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5427-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="d5427-103">Mřížku vlastností pro uživatelské nastavení můžete vytvořit naplněním ovládacího prvku <xref:System.Windows.Forms.PropertyGrid> pomocí vlastností uživatelského nastavení objektu `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="d5427-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5427-104">Aby tento příklad fungoval, musí mít vaše aplikace nastavené uživatelské nastavení.</span><span class="sxs-lookup"><span data-stu-id="d5427-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="d5427-105">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d5427-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="d5427-106">Objekt `My.Settings` zpřístupňuje každé nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d5427-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="d5427-107">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení.</span><span class="sxs-lookup"><span data-stu-id="d5427-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="d5427-108">**Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení rozsahu **uživatele**je pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="d5427-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="d5427-109">Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="d5427-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5427-110">V době běhu nemůžete změnit ani uložit hodnoty nastavení rozsahu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5427-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="d5427-111">Nastavení rozsahu aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5427-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="d5427-112">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="d5427-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="d5427-113">Tento příklad používá ovládací prvek <xref:System.Windows.Forms.PropertyGrid> pro přístup k vlastnostem uživatelského nastavení objektu `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="d5427-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="d5427-114">Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti objektu `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="d5427-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="d5427-115">Vlastnosti uživatelského nastavení ale mají atribut <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d5427-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="d5427-116">V tomto příkladu se nastaví vlastnost <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> <xref:System.Windows.Forms.PropertyGrid> na <xref:System.Configuration.UserScopedSettingAttribute>, aby se zobrazily pouze vlastnosti uživatelského nastavení.</span><span class="sxs-lookup"><span data-stu-id="d5427-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="d5427-117">Přidání mřížky vlastností uživatelského nastavení</span><span class="sxs-lookup"><span data-stu-id="d5427-117">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="d5427-118">Přidejte ovládací prvek **PropertyGrid** ze **sady nástrojů** na návrhovou plochu pro vaši aplikaci, která se předpokládá `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d5427-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="d5427-119">Výchozí název ovládacího prvku mřížky vlastnosti je `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="d5427-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="d5427-120">Dvojím kliknutím na návrhovou plochu pro `Form1` otevřete kód pro obslužnou rutinu události načtení formuláře.</span><span class="sxs-lookup"><span data-stu-id="d5427-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="d5427-121">Nastavte objekt `My.Settings` jako vybraný objekt pro mřížku vlastností.</span><span class="sxs-lookup"><span data-stu-id="d5427-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="d5427-122">Nakonfigurujte mřížku vlastností tak, aby zobrazovala pouze uživatelská nastavení.</span><span class="sxs-lookup"><span data-stu-id="d5427-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="d5427-123">Chcete-li zobrazit pouze nastavení rozsahu aplikace, použijte atribut <xref:System.Configuration.ApplicationScopedSettingAttribute> místo <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d5427-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d5427-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d5427-124">Robust Programming</span></span>  

 <span data-ttu-id="d5427-125">Aplikace uloží nastavení uživatele, když se aplikace vypíná.</span><span class="sxs-lookup"><span data-stu-id="d5427-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="d5427-126">Chcete-li nastavení uložit hned, zavolejte metodu `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="d5427-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="d5427-127">Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d5427-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5427-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5427-128">See also</span></span>

- [<span data-ttu-id="d5427-129">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="d5427-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="d5427-130">Postupy: čtení nastavení aplikace v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5427-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="d5427-131">Postupy: Změna uživatelského nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5427-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="d5427-132">Postupy: zachování uživatelských nastavení v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5427-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="d5427-133">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="d5427-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
