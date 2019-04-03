---
title: 'Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 20c475fd7bd4b2cec6c6e10182a88a43fa7c56f1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843042"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="16bcf-102">Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16bcf-102">How to: Create Property Grids for User Settings in Visual Basic</span></span>
<span data-ttu-id="16bcf-103">Můžete vytvořit mřížku vlastností pro uživatelská nastavení naplněním <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku pomocí vlastnosti nastavení uživatele `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="16bcf-103">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16bcf-104">Aby tento příklad fungoval musí mít vaše aplikace nastavené uživatelské nastavení.</span><span class="sxs-lookup"><span data-stu-id="16bcf-104">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="16bcf-105">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="16bcf-105">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="16bcf-106">`My.Settings` Objekt poskytuje každému nastavení jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16bcf-106">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="16bcf-107">Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typů nastavení.</span><span class="sxs-lookup"><span data-stu-id="16bcf-107">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="16bcf-108">Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace**– obor nastavení je jen pro čtení, při vlastnost pro **uživatele**– oboru nastavení je pro čtení i zápis.</span><span class="sxs-lookup"><span data-stu-id="16bcf-108">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="16bcf-109">Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="16bcf-109">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16bcf-110">Nelze změnit ani uložit hodnoty nastavení oboru aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="16bcf-110">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="16bcf-111">Nastavení oboru aplikace lze změnit pouze při vytváření aplikace (prostřednictvím **Návrháře projektu**) nebo úpravou konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="16bcf-111">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="16bcf-112">Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="16bcf-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="16bcf-113">Tento příklad používá <xref:System.Windows.Forms.PropertyGrid> ovládací prvek pro přístup k vlastnostem nastavení uživatele `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="16bcf-113">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="16bcf-114">Ve výchozím nastavení <xref:System.Windows.Forms.PropertyGrid> zobrazuje všechny vlastnosti `My.Settings` objektu.</span><span class="sxs-lookup"><span data-stu-id="16bcf-114">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="16bcf-115">Ale mít vlastnosti uživatelského nastavení <xref:System.Configuration.UserScopedSettingAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="16bcf-115">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="16bcf-116">Tento příklad nastaví <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> vlastnost <xref:System.Windows.Forms.PropertyGrid> k <xref:System.Configuration.UserScopedSettingAttribute> zobrazit pouze vlastnosti nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="16bcf-116">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="16bcf-117">Chcete-li přidat mřížky vlastností uživatelské nastavení</span><span class="sxs-lookup"><span data-stu-id="16bcf-117">To add a user setting property grid</span></span>  
  
1.  <span data-ttu-id="16bcf-118">Přidat **PropertyGrid** ovládacího prvku **nástrojů** na návrhovou plochu pro vaši aplikaci, předpokládá, že tady být `Form1`.</span><span class="sxs-lookup"><span data-stu-id="16bcf-118">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="16bcf-119">Výchozí název ovládacího prvku mřížky vlastností je `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="16bcf-119">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2.  <span data-ttu-id="16bcf-120">Klikněte dvakrát na návrhové ploše pro `Form1` otevřete kód pro obslužnou rutinu události nahrání formuláře.</span><span class="sxs-lookup"><span data-stu-id="16bcf-120">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3.  <span data-ttu-id="16bcf-121">Nastavte `My.Settings` objektu jako vybraného objektu mřížky vlastností.</span><span class="sxs-lookup"><span data-stu-id="16bcf-121">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4.  <span data-ttu-id="16bcf-122">Nakonfigurujte mřížkou zobrazí pouze nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="16bcf-122">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    >  <span data-ttu-id="16bcf-123">Chcete-li zobrazit pouze nastavení oboru aplikace, použijte <xref:System.Configuration.ApplicationScopedSettingAttribute> atribut namísto <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="16bcf-123">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="16bcf-124">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="16bcf-124">Robust Programming</span></span>  
 <span data-ttu-id="16bcf-125">Aplikace ukládá uživatelská nastavení při ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="16bcf-125">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="16bcf-126">Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metody.</span><span class="sxs-lookup"><span data-stu-id="16bcf-126">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="16bcf-127">Další informace najdete v tématu [jak: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="16bcf-127">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bcf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16bcf-128">See also</span></span>

- [<span data-ttu-id="16bcf-129">Objekt My.Settings</span><span class="sxs-lookup"><span data-stu-id="16bcf-129">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="16bcf-130">Postupy: Čtení nastavení aplikace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16bcf-130">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="16bcf-131">Postupy: Změna uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16bcf-131">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="16bcf-132">Postupy: Zachování uživatelského nastavení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16bcf-132">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="16bcf-133">Správa nastavení aplikace (.NET)</span><span class="sxs-lookup"><span data-stu-id="16bcf-133">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
