---
title: Balení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: 4212f58c39f63be6ba20c3b79e5d9c98d0615c5e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43487153"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="449f8-102">Zabalení a nasazení vlastních rozšíření oboru názvů My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="449f8-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="449f8-103">Visual Basic poskytuje jednoduchý způsob nasazení vaší vlastní `My` rozšíření oboru názvů pomocí šablony sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="449f8-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="449f8-104">Pokud vytváříte šablonu projektu pro kterou vaše `My` rozšíření jsou nedílnou součástí toho nový typ projektu, můžete zahrnout pouze váš vlastní `My` kódu rozšíření s projektem při exportu šablony.</span><span class="sxs-lookup"><span data-stu-id="449f8-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="449f8-105">Další informace o exportu šablony projektů, naleznete v tématu [postupy: vytváření šablon projektu](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="449f8-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="449f8-106">Pokud vaše vlastní `My` rozšíření je v souboru jednoho kódu, můžete exportovat soubor šablony položky, které uživatelé můžou přidávat na libovolný typ projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="449f8-107">Potom můžete přizpůsobit šablonu položky povolit další funkce a chování pro vaše vlastní `My` rozšíření v projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="449f8-108">Tyto možnosti patří:</span><span class="sxs-lookup"><span data-stu-id="449f8-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="449f8-109">Umožňuje uživatelům spravovat své vlastní `My` rozšíření **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="449f8-110">Automatické přidávání vlastních `My` rozšíření při odkazu na zadané sestavení se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="449f8-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="449f8-111">Skrytí `My` šablonu položky rozšíření v **přidat položku** dialogové okno tak, aby není zahrnutý v seznamu položek projektu.</span><span class="sxs-lookup"><span data-stu-id="449f8-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="449f8-112">Toto téma popisuje, jak zabalit vlastní `My` rozšíření jako skrytá položka šablonu, která se dají spravovat z **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="449f8-113">Vlastní `My` rozšíření můžete také přidat automaticky při přidání do projektu odkaz na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="449f8-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="449f8-114">Vytvoření rozšíření rozhraní My namespace</span><span class="sxs-lookup"><span data-stu-id="449f8-114">Create a My namespace extension</span></span>

<span data-ttu-id="449f8-115">Prvním krokem při vytváření balíčku pro nasazení, aby vlastní `My` rozšíření je pro vytvoření rozšíření jako soubor jeden kód.</span><span class="sxs-lookup"><span data-stu-id="449f8-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="449f8-116">Podrobnosti a pokyny o tom, jak vytvořit vlastní `My` rozšíření, naleznete v tématu [rozšíření My Namespace v jazyce Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="449f8-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="449f8-117">Exportovat rozšíření rozhraní My namespace jako šablonu položky</span><span class="sxs-lookup"><span data-stu-id="449f8-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="449f8-118">Až budete mít soubor kódu, který obsahuje vaše `My` rozšíření oboru názvů, můžete exportovat soubor kódu jako šablonu položky sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="449f8-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="449f8-119">Pokyny o tom, jak exportovat soubor jako šablonu položky sady Visual Studio najdete v tématu [postupy: vytváření šablon položek](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="449f8-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="449f8-120">Pokud vaše `My` rozšíření oboru názvů závislý na konkrétní sestavení, můžete přizpůsobit vaši šablonu položky automaticky instalovat vaši `My` rozšíření oboru názvů při přidání odkazu na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="449f8-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="449f8-121">Díky tomu budete chtít vyloučit tento odkaz na sestavení, když je soubor kódu exportovat jako šablonu položky sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="449f8-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="449f8-122">Přizpůsobení šablony položky</span><span class="sxs-lookup"><span data-stu-id="449f8-122">Customize the item template</span></span>

<span data-ttu-id="449f8-123">Můžete povolit položku šablony pro správu z **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="449f8-124">Můžete také povolit šablony položky se automaticky přidá, když se do projektu přidá odkaz na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="449f8-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="449f8-125">Pokud chcete povolit tyto úpravy, přidáte nový soubor, Soubor CustomData do šablony a pak přidejte nový prvek do souboru XML v souboru .vstemplate.</span><span class="sxs-lookup"><span data-stu-id="449f8-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="449f8-126">Přidat soubor CustomData</span><span class="sxs-lookup"><span data-stu-id="449f8-126">Add the CustomData file</span></span>

<span data-ttu-id="449f8-127">Soubor CustomData je textový soubor, který má příponu názvu souboru. CustomData (název souboru lze nastavit na libovolnou hodnotu smysluplné do šablony), který obsahuje XML.</span><span class="sxs-lookup"><span data-stu-id="449f8-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="449f8-128">Kód XML v souboru CustomData instruuje Visual Basic pro zahrnutí vaší `My` rozšíření uživatelé budou používat **Moje rozšíření** stránky Návrháře projektu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="449f8-129">Volitelně můžete přidat <`AssemblyFullName>` atribut CustomData souboru XML.</span><span class="sxs-lookup"><span data-stu-id="449f8-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="449f8-130">Toto dá pokyn jazyka Visual Basic můžete automaticky nainstalovat vlastní `My` rozšíření při odkazu na konkrétní sestavení je přidána do projektu.</span><span class="sxs-lookup"><span data-stu-id="449f8-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="449f8-131">Můžete použít libovolný textového editoru nebo editoru XML k vytvoření souboru CustomData a poté jej přidejte do šablony položky komprimovanou složku (ZIP).</span><span class="sxs-lookup"><span data-stu-id="449f8-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="449f8-132">Například následující kód XML ukazuje obsah souboru CustomData, který se přidá šablonu položky do složky Moje rozšíření systému projektu jazyka Visual Basic, pokud odkaz na sestavení Microsoft.VisualBasic.PowerPacks.Vs.dll se přidá do projektu.</span><span class="sxs-lookup"><span data-stu-id="449f8-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="449f8-133">Obsahuje soubor CustomData <`VBMyExtensionTemplate>` element, který má atributy, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="449f8-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="449f8-134">Atribut</span><span class="sxs-lookup"><span data-stu-id="449f8-134">Attribute</span></span>|<span data-ttu-id="449f8-135">Popis</span><span class="sxs-lookup"><span data-stu-id="449f8-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="449f8-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="449f8-136">Required.</span></span> <span data-ttu-id="449f8-137">Jedinečný identifikátor pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="449f8-137">A unique identifier for the extension.</span></span> <span data-ttu-id="449f8-138">Pokud rozšíření, která má toto ID již byla přidána do projektu, uživatel nebude vyzván znovu přidat.</span><span class="sxs-lookup"><span data-stu-id="449f8-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="449f8-139">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="449f8-139">Required.</span></span> <span data-ttu-id="449f8-140">Číslo verze pro šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="449f8-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="449f8-141">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="449f8-141">Optional.</span></span> <span data-ttu-id="449f8-142">Název sestavení.</span><span class="sxs-lookup"><span data-stu-id="449f8-142">An assembly name.</span></span> <span data-ttu-id="449f8-143">Když do projektu se přidá odkaz na toto sestavení, uživateli zobrazí výzva k přidání `My` rozšíření z této šablony položky.</span><span class="sxs-lookup"><span data-stu-id="449f8-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="449f8-144">Přidat \<CustomDataSignature > element k souboru .vstemplate</span><span class="sxs-lookup"><span data-stu-id="449f8-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="449f8-145">K identifikaci vaší šablony položky sady Visual Studio `My` rozšíření oboru názvů, musíte také upravit soubor .vstemplate šablony položky.</span><span class="sxs-lookup"><span data-stu-id="449f8-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="449f8-146">Je nutné přidat `<CustomDataSignature>` elementu `<TemplateData>` elementu.</span><span class="sxs-lookup"><span data-stu-id="449f8-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="449f8-147">`<CustomDataSignature>` Element musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="449f8-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="449f8-148">Soubory v komprimované složce (.zip soubor) nemůžete upravovat přímo.</span><span class="sxs-lookup"><span data-stu-id="449f8-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="449f8-149">Musí zkopírovat soubor .vstemplate ze složky komprimované, upravte ho a soubor .vstemplate v komprimované složce nahraďte aktualizovanou kopii.</span><span class="sxs-lookup"><span data-stu-id="449f8-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="449f8-150">Následující příklad ukazuje obsah souboru .vstemplate, který má `<CustomDataSignature>` element přidat.</span><span class="sxs-lookup"><span data-stu-id="449f8-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="449f8-151">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="449f8-151">Install the template</span></span>

<span data-ttu-id="449f8-152">Instalace šablony, můžete zkopírovat komprimovanou složku (*ZIP* soubor) do složky šablony položky Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="449f8-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="449f8-153">Ve výchozím nastavení, šablon položek uživatele jsou umístěny v *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="449f8-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="449f8-154">Alternativně můžete publikovat šablony jako instalační program Visual Studio (*.vsi*) soubor.</span><span class="sxs-lookup"><span data-stu-id="449f8-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="449f8-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="449f8-155">See also</span></span>

- [<span data-ttu-id="449f8-156">Rozšíření My Namespace v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="449f8-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="449f8-157">Rozšíření aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="449f8-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="449f8-158">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="449f8-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="449f8-159">Stránka Moje rozšíření, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="449f8-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
