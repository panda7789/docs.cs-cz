---
title: Balení a nasazení vlastních rozšíření
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330262"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="539ab-102">Zabalit a nasadit vlastní moje rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="539ab-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="539ab-103">Visual Basic poskytuje snadný způsob, jak nasadit vlastní `My` rozšíření oboru názvů pomocí šablon sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="539ab-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="539ab-104">Pokud vytváříte šablonu projektu, pro kterou jsou vaše `My` rozšíření nedílnou součástí nového typu projektu, můžete při exportu šablony do projektu zahrnout pouze vlastní `My` kód rozšíření.</span><span class="sxs-lookup"><span data-stu-id="539ab-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="539ab-105">Další informace o exportu šablon projektů naleznete v tématu [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="539ab-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="539ab-106">Pokud je vaše `My` vlastní rozšíření v jednom souboru kódu, můžete soubor exportovat jako šablonu položky, kterou mohou uživatelé přidat do libovolného typu Visual Basic projektu.</span><span class="sxs-lookup"><span data-stu-id="539ab-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="539ab-107">Pak můžete přizpůsobit šablonu položky a povolit tak další možnosti a chování pro vlastní `My` rozšíření v projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="539ab-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="539ab-108">Mezi tyto možnosti patří následující:</span><span class="sxs-lookup"><span data-stu-id="539ab-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="539ab-109">Umožnění uživatelům spravovat vlastní `My` rozšíření ze stránky **Moje rozšíření** v Návrháři projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="539ab-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="539ab-110">Pokud se do projektu `My` přidá odkaz na zadané sestavení, automaticky se přidá vlastní rozšíření.</span><span class="sxs-lookup"><span data-stu-id="539ab-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="539ab-111">Skrytí šablony `My` položky rozšíření v dialogovém okně **Přidat položku** tak, aby není zahrnuto v seznamu položek projektu.</span><span class="sxs-lookup"><span data-stu-id="539ab-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="539ab-112">Toto téma popisuje, jak zabalit `My` vlastní rozšíření jako skrytou šablonu položky, kterou lze spravovat ze stránky **Moje rozšíření** v Návrháři projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="539ab-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="539ab-113">Vlastní `My` rozšíření lze také přidat automaticky, pokud je do projektu přidán odkaz na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="539ab-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="539ab-114">Vytvoření rozšíření My Namespace</span><span class="sxs-lookup"><span data-stu-id="539ab-114">Create a My namespace extension</span></span>

<span data-ttu-id="539ab-115">Prvním krokem při vytváření balíčku pro nasazení pro vlastní `My` rozšíření je vytvořit rozšíření jako jeden soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="539ab-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="539ab-116">Podrobnosti a pokyny, jak vytvořit vlastní `My` rozšíření, najdete v tématu [rozšíření oboru názvů My v Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="539ab-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="539ab-117">Exportovat rozšíření My Namespace jako šablonu položky</span><span class="sxs-lookup"><span data-stu-id="539ab-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="539ab-118">Až budete mít soubor kódu, který obsahuje rozšíření `My` oboru názvů, můžete soubor kódu exportovat jako šablonu položky sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="539ab-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="539ab-119">Pokyny, jak exportovat soubor jako šablonu položky sady Visual Studio, naleznete v tématu [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="539ab-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="539ab-120">Pokud rozšíření `My` oboru názvů má závislost na konkrétní sestavení, můžete přizpůsobit šablonu položky tak, aby automaticky instalovala rozšíření `My` oboru názvů, když je přidán odkaz na toto sestavení.</span><span class="sxs-lookup"><span data-stu-id="539ab-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="539ab-121">V důsledku toho budete chtít vyloučit tento odkaz na sestavení, když exportujete soubor kódu jako šablonu položky sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="539ab-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="539ab-122">Přizpůsobení šablony položky</span><span class="sxs-lookup"><span data-stu-id="539ab-122">Customize the item template</span></span>

<span data-ttu-id="539ab-123">Šablonu položky můžete povolit, aby byla spravována ze stránky **Moje rozšíření** návrháře projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="539ab-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="539ab-124">Můžete také povolit automatické přidání šablony položky, když je do projektu přidán odkaz na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="539ab-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="539ab-125">Chcete-li povolit tato přizpůsobení, přidejte do šablony nový soubor, označovaný jako soubor CustomData, a poté přidejte nový prvek do XML v souboru. vstemplate.</span><span class="sxs-lookup"><span data-stu-id="539ab-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="539ab-126">Přidat soubor CustomData</span><span class="sxs-lookup"><span data-stu-id="539ab-126">Add the CustomData file</span></span>

<span data-ttu-id="539ab-127">Soubor CustomData je textový soubor, který má příponu názvu souboru. CustomData (název souboru může být nastaven na libovolnou hodnotu smysluplnou pro šablonu) a obsahující XML.</span><span class="sxs-lookup"><span data-stu-id="539ab-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="539ab-128">XML v souboru CustomData instruuje Visual Basic, aby zahrnovalo vaše `My` rozšíření, když uživatelé použijí stránku **Moje rozšíření** Návrháře projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="539ab-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="539ab-129">Volitelně můžete přidat atribut <`AssemblyFullName>` do souboru XML CustomData.</span><span class="sxs-lookup"><span data-stu-id="539ab-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="539ab-130">Tímto dáte pokyn Visual Basic k automatické instalaci vlastního `My` rozšíření, když je do projektu přidán odkaz na konkrétní sestavení.</span><span class="sxs-lookup"><span data-stu-id="539ab-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="539ab-131">Pomocí libovolného textového editoru nebo editoru XML můžete vytvořit soubor CustomData a pak ho přidat do komprimované složky šablony položky (soubor ZIP).</span><span class="sxs-lookup"><span data-stu-id="539ab-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="539ab-132">Například následující kód XML ukazuje obsah souboru CustomData, který přidá položku šablony do složky Moje rozšíření v projektu Visual Basic, když se do projektu přidá odkaz na sestavení Microsoft. VisualBasic. PowerPacks. vs. dll.</span><span class="sxs-lookup"><span data-stu-id="539ab-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="539ab-133">Soubor CustomData obsahuje <`VBMyExtensionTemplate>` element, který má atributy uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="539ab-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="539ab-134">Atribut</span><span class="sxs-lookup"><span data-stu-id="539ab-134">Attribute</span></span>|<span data-ttu-id="539ab-135">Popis</span><span class="sxs-lookup"><span data-stu-id="539ab-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="539ab-136">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="539ab-136">Required.</span></span> <span data-ttu-id="539ab-137">Jedinečný identifikátor pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="539ab-137">A unique identifier for the extension.</span></span> <span data-ttu-id="539ab-138">Pokud rozšíření s tímto ID již bylo do projektu přidáno, uživatel nebude vyzván k jeho přidání.</span><span class="sxs-lookup"><span data-stu-id="539ab-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="539ab-139">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="539ab-139">Required.</span></span> <span data-ttu-id="539ab-140">Číslo verze pro šablonu položky</span><span class="sxs-lookup"><span data-stu-id="539ab-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="539ab-141">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="539ab-141">Optional.</span></span> <span data-ttu-id="539ab-142">Název sestavení.</span><span class="sxs-lookup"><span data-stu-id="539ab-142">An assembly name.</span></span> <span data-ttu-id="539ab-143">Pokud je do projektu přidán odkaz na toto sestavení, bude uživatel vyzván k přidání `My` rozšíření z této šablony položky.</span><span class="sxs-lookup"><span data-stu-id="539ab-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="539ab-144">Přidat element \<CustomDataSignature –> do souboru. vstemplate</span><span class="sxs-lookup"><span data-stu-id="539ab-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="539ab-145">Chcete-li identifikovat šablonu položky sady Visual Studio `My` jako rozšíření oboru názvů, je nutné také upravit soubor. vstemplate pro šablonu položky.</span><span class="sxs-lookup"><span data-stu-id="539ab-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="539ab-146">Je nutné přidat `<CustomDataSignature>` prvek do `<TemplateData>` prvku.</span><span class="sxs-lookup"><span data-stu-id="539ab-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="539ab-147">`<CustomDataSignature>` Element musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="539ab-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="539ab-148">Soubory nelze upravovat v komprimované složce (soubor. zip) přímo.</span><span class="sxs-lookup"><span data-stu-id="539ab-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="539ab-149">Je nutné zkopírovat soubor. vstemplate z komprimované složky, upravit ho a pak nahradit soubor. vstemplate v komprimované složce pomocí aktualizované kopie.</span><span class="sxs-lookup"><span data-stu-id="539ab-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="539ab-150">Následující příklad ukazuje obsah souboru. vstemplate, který má přidaný `<CustomDataSignature>` element.</span><span class="sxs-lookup"><span data-stu-id="539ab-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

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

## <a name="install-the-template"></a><span data-ttu-id="539ab-151">Instalace šablony</span><span class="sxs-lookup"><span data-stu-id="539ab-151">Install the template</span></span>

<span data-ttu-id="539ab-152">Chcete-li nainstalovat šablonu, můžete zkopírovat komprimovanou složku (soubor *. zip* ) do složky šablony Visual Basic položek.</span><span class="sxs-lookup"><span data-stu-id="539ab-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="539ab-153">Ve výchozím nastavení se šablony uživatelských položek nacházejí v *%UserProfile%\Documents\Visual studiu \<verze\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="539ab-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="539ab-154">Alternativně můžete šablonu publikovat jako soubor Instalační program pro Visual Studio (*. vsi*).</span><span class="sxs-lookup"><span data-stu-id="539ab-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="539ab-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="539ab-155">See also</span></span>

- [<span data-ttu-id="539ab-156">Rozšíření oboru názvů My v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="539ab-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="539ab-157">Rozšíření aplikačního modelu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="539ab-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="539ab-158">Přizpůsobení výběru objektů dostupných v oboru názvů My</span><span class="sxs-lookup"><span data-stu-id="539ab-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="539ab-159">Stránka Moje rozšíření, návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="539ab-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
