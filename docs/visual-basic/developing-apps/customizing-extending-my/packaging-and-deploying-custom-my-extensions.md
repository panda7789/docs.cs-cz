---
title: Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 901d0b80a18d2f4d262cc65eb485dcc628bc6a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591856"
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="fec69-102">Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fec69-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="fec69-103">Visual Basic poskytuje snadný způsob můžete nasadit vaše vlastní `My` rozšíření oboru názvů pomocí šablony sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fec69-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="fec69-104">Pokud vytváříte šablona projektu pro kterou vaše `My` rozšíření jsou nedílnou součástí nového typu projektu, můžete zahrnout pouze vaše vlastní `My` kód rozšíření projektu při exportu šablony.</span><span class="sxs-lookup"><span data-stu-id="fec69-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="fec69-105">Další informace o exportu šablony projektů najdete v tématu [postupy: vytvoření šablony projektů](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="fec69-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>  
  
 <span data-ttu-id="fec69-106">Pokud vaše vlastní `My` rozšíření je v souboru jednoho kódu, můžete exportovat soubor jako šablonu položky, které můžete přidat uživatele k libovolnému typu projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="fec69-107">Následně můžete přizpůsobit šablony položky, chcete-li povolit další funkce a chování pro vaše vlastní `My` rozšíření v projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="fec69-108">Tyto funkce patří:</span><span class="sxs-lookup"><span data-stu-id="fec69-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="fec69-109">Umožňuje uživatelům spravovat vaše vlastní `My` rozšíření **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="fec69-110">Automatické přidávání vašich vlastních `My` příponu při odkaz na zadaná sestavení je přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="fec69-111">Skrytí `My` rozšíření šablony položky v **přidat položku** dialogu tak, aby není zahrnutý v seznamu položek projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="fec69-112">Toto téma popisuje, jak zabalit vlastní `My` rozšíření jako šablonu skrytá položka, kterou je možné spravovat z **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fec69-113">Vlastní `My` rozšíření můžete také přidat automaticky při přidání odkazu na zadaná sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="fec69-114">Vytvoření rozšíření oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="fec69-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="fec69-115">Prvním krokem při vytváření balíčku pro nasazení pro vlastní `My` rozšíření je pro vytvoření rozšíření jako soubor jednoho kódu.</span><span class="sxs-lookup"><span data-stu-id="fec69-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="fec69-116">Podrobnosti a pokyny o tom, jak vytvořit vlastní `My` rozšíření, najdete v části [rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="fec69-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="fec69-117">Export rozšíření oboru názvů My jako šablonu položky</span><span class="sxs-lookup"><span data-stu-id="fec69-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="fec69-118">Až budete mít soubor kód, který zahrnuje vaše `My` rozšíření oboru názvů, můžete exportovat soubor kódu jako šablonu položky Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fec69-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="fec69-119">Pokyny o tom, jak exportovat soubor jako šablonu položky Visual Studio najdete v tématu [postupy: vytváření šablon položek](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="fec69-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fec69-120">Pokud vaše `My` rozšíření oboru názvů má závislost na určitém sestavení, můžete upravit položku šablony můžete automaticky nainstalovat vaší `My` rozšíření oboru názvů, pokud je přidán odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fec69-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="fec69-121">Výsledkem je budete chtít vyloučit tento odkaz na sestavení, při exportu souboru kódu jako šablonu položky Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fec69-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="fec69-122">Přizpůsobení šablony položek</span><span class="sxs-lookup"><span data-stu-id="fec69-122">Customize the item template</span></span>  
 <span data-ttu-id="fec69-123">Můžete povolit šabloně položka pro správu z **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fec69-124">Můžete také povolit šablonu položky pro automaticky přidá, když je odkaz na zadaná sestavení přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="fec69-125">Pokud chcete povolit toto vlastní nastavení, přidáte nového souboru s názvem souboru CustomData do šablony a poté přidejte nový element jazyka XML v souboru .vstemplate.</span><span class="sxs-lookup"><span data-stu-id="fec69-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="fec69-126">Přidejte soubor CustomData</span><span class="sxs-lookup"><span data-stu-id="fec69-126">Add the CustomData file</span></span>  
 <span data-ttu-id="fec69-127">CustomData soubor je textový soubor, který má příponu názvu souboru. CustomData (název souboru lze nastavit na jakoukoli hodnotu smysluplnou) a který obsahuje XML.</span><span class="sxs-lookup"><span data-stu-id="fec69-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="fec69-128">Kód XML v souboru CustomData dá pokyn, Visual Basic pro zahrnutí vaše `My` rozšíření uživatelům při používání **Moje rozšíření** stránky v Návrháři projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fec69-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="fec69-129">Volitelně můžete přidat <`AssemblyFullName>` atribut CustomData souboru XML.</span><span class="sxs-lookup"><span data-stu-id="fec69-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="fec69-130">Tím se nastaví jazyka Visual Basic můžete automaticky nainstalovat vaše vlastní `My` příponu při odkaz na konkrétní sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="fec69-131">Můžete použít k vytvoření souboru CustomData žádné textového editoru nebo editoru XML a poté jej přidejte do šablony položky komprimované složce (.zip soubor).</span><span class="sxs-lookup"><span data-stu-id="fec69-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="fec69-132">Například následující kód XML zobrazí obsah souboru CustomData, který se přidá šablonu položky do složky Moje rozšíření v projektu jazyka Visual Basic, když odkaz na sestavení Microsoft.VisualBasic.PowerPacks.Vs.dll se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="fec69-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="fec69-133">Obsahuje soubor CustomData <`VBMyExtensionTemplate>` element, který má atributy uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fec69-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="fec69-134">Atribut</span><span class="sxs-lookup"><span data-stu-id="fec69-134">Attribute</span></span>|<span data-ttu-id="fec69-135">Popis</span><span class="sxs-lookup"><span data-stu-id="fec69-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="fec69-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fec69-136">Required.</span></span> <span data-ttu-id="fec69-137">Jedinečný identifikátor pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="fec69-137">A unique identifier for the extension.</span></span> <span data-ttu-id="fec69-138">Pokud rozšíření, která má toto ID již byla přidána do projektu, uživatel nebude vyzván ji znovu přidejte.</span><span class="sxs-lookup"><span data-stu-id="fec69-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="fec69-139">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fec69-139">Required.</span></span> <span data-ttu-id="fec69-140">Číslo verze šablony položky.</span><span class="sxs-lookup"><span data-stu-id="fec69-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="fec69-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fec69-141">Optional.</span></span> <span data-ttu-id="fec69-142">Název sestavení.</span><span class="sxs-lookup"><span data-stu-id="fec69-142">An assembly name.</span></span> <span data-ttu-id="fec69-143">Když odkaz na toto sestavení se přidá do projektu, uživatel bude vyzváni k přidání `My` rozšíření z této šablony položky.</span><span class="sxs-lookup"><span data-stu-id="fec69-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="fec69-144">Přidat \<CustomDataSignature > elementu, který chcete soubor .vstemplate</span><span class="sxs-lookup"><span data-stu-id="fec69-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="fec69-145">K identifikaci vaší šablony položek sady Visual Studio `My` rozšíření oboru názvů, musíte také upravit soubor .vstemplate položky šablony.</span><span class="sxs-lookup"><span data-stu-id="fec69-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="fec69-146">Je nutné přidat `<CustomDataSignature>` elementu, který chcete `<TemplateData>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fec69-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="fec69-147">`<CustomDataSignature>` Element musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fec69-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="fec69-148">Soubory v komprimované složce (.zip soubor) nelze upravovat přímo.</span><span class="sxs-lookup"><span data-stu-id="fec69-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="fec69-149">Musíte zkopírovat soubor .vstemplate z komprimované složky, upravte ho a potom můžete nahradit soubor .vstemplate v komprimované složce aktualizovanou kopií.</span><span class="sxs-lookup"><span data-stu-id="fec69-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="fec69-150">Následující příklad ukazuje obsah .vstemplate soubor, který má `<CustomDataSignature>` elementu přidány.</span><span class="sxs-lookup"><span data-stu-id="fec69-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a><span data-ttu-id="fec69-151">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="fec69-151">Install the template</span></span>  
 <span data-ttu-id="fec69-152">Instalace šablony, můžete zkopírovat komprimované složce (.zip soubor) do složky šablon položek jazyka Visual Basic (například Dokumenty\visual 2008\Templates\Item Templates\Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="fec69-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="fec69-153">Alternativně můžete publikovat šablony jako soubor Instalační program Visual Studio (.vsi).</span><span class="sxs-lookup"><span data-stu-id="fec69-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec69-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="fec69-154">See also</span></span>  
 [<span data-ttu-id="fec69-155">Rozšíření My Namespace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fec69-155">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [<span data-ttu-id="fec69-156">Rozšíření aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fec69-156">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [<span data-ttu-id="fec69-157">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="fec69-157">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [<span data-ttu-id="fec69-158">Stránka Moje rozšíření, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="fec69-158">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
