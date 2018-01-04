---
title: "Atributy a komentáře lokalizace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85584c17675167d374c595aa26288f550a033efb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="localization-attributes-and-comments"></a><span data-ttu-id="408b5-102">Atributy a komentáře lokalizace</span><span class="sxs-lookup"><span data-stu-id="408b5-102">Localization Attributes and Comments</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="408b5-103">lokalizace komentáře jsou vlastnosti, uvnitř [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód, poskytuje vývojářům poskytovat pravidly a tipy pro lokalizaci.</span><span class="sxs-lookup"><span data-stu-id="408b5-103"> localization comments are properties, inside [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] source code, supplied by developers to provide rules and hints for localization.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="408b5-104">lokalizace komentáře obsahovat dvě sady informace: atributy lokalizovatelnost a lokalizace vlastní komentáře.</span><span class="sxs-lookup"><span data-stu-id="408b5-104"> localization comments contain two sets of information: localizability attributes and free-form localization comments.</span></span> <span data-ttu-id="408b5-105">Lokalizovatelnost atributy jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace rozhraní API k označení prostředků, které jsou lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="408b5-105">Localizability attributes are used by the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Localization API to indicate which resources are to be localized.</span></span> <span data-ttu-id="408b5-106">Vlastní komentáře jsou veškeré informace, které chce zahrnují vytváření aplikací.</span><span class="sxs-lookup"><span data-stu-id="408b5-106">Free-form comments are any information that the application author wants to include.</span></span>  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a><span data-ttu-id="408b5-107">Lokalizace komentáře</span><span class="sxs-lookup"><span data-stu-id="408b5-107">Localization Comments</span></span>  
 <span data-ttu-id="408b5-108">Pokud kód aplikace autoři mít požadavky na konkrétní elementy v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], jako je například omezení délka textu, rodinu písem a velikost písma, se může nesou tyto informace k překladatelům při lokalizaci s komentáři v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="408b5-108">If markup application authors have requirements for specific elements in [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], such as constraints on text length, font family, or font size, they can convey this information to localizers with comments in the [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] code.</span></span> <span data-ttu-id="408b5-109">Proces přidávání komentářů ke zdrojovému kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="408b5-109">The process for adding comments to source code is as follows:</span></span>  
  
1.  <span data-ttu-id="408b5-110">Vývojář aplikace přidá lokalizace komentáře [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="408b5-110">Application developer adds localization comments to [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] source code.</span></span>  
  
2.  <span data-ttu-id="408b5-111">Během procesu sestavení můžete určit, v souboru .proj zda psát komentáře volného formátu lokalizace v sestavení, pruhu se součástí komentáře nebo pruhu se všechny komentáře.</span><span class="sxs-lookup"><span data-stu-id="408b5-111">During the build process, you can specify in the .proj file whether to leave the free-form localization comments in the assembly, strip out part of the comments, or strip out all the comments.</span></span> <span data-ttu-id="408b5-112">Odstraní se na komentáře jsou umístěny v samostatném souboru.</span><span class="sxs-lookup"><span data-stu-id="408b5-112">The stripped-out comments are placed in a separate file.</span></span> <span data-ttu-id="408b5-113">Zadejte vaše možnost použití `LocalizationDirectivesToLocFile` značka, např:</span><span class="sxs-lookup"><span data-stu-id="408b5-113">You specify your option using a `LocalizationDirectivesToLocFile` tag, eg:</span></span>  
  
     <span data-ttu-id="408b5-114">`<LocalizationDirectivesToLocFile>`*hodnotu*`</LocalizationDirectivesToLocFile>`</span><span class="sxs-lookup"><span data-stu-id="408b5-114">`<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`</span></span>  
  
3.  <span data-ttu-id="408b5-115">Hodnoty, které mohou být přiřazeny jsou:</span><span class="sxs-lookup"><span data-stu-id="408b5-115">The values that can be assigned are:</span></span>  
  
    -   <span data-ttu-id="408b5-116">**Žádný** – jak komentářů a atributů zůstane uvnitř sestavení a je generována žádný samostatný soubor.</span><span class="sxs-lookup"><span data-stu-id="408b5-116">**None** - Both comments and attributes stay inside the assembly and no separate file is generated.</span></span>  
  
    -   <span data-ttu-id="408b5-117">**CommentsOnly** – odstraní pouze komentáře od sestavení a umístí je do samostatné LocFile.</span><span class="sxs-lookup"><span data-stu-id="408b5-117">**CommentsOnly** - Strips only the comments from the assembly and places them in the separate LocFile.</span></span>  
  
    -   <span data-ttu-id="408b5-118">**Všechny** – odstraní komentářů a atributů ze sestavení a umístí je i v samostatných LocFile.</span><span class="sxs-lookup"><span data-stu-id="408b5-118">**All** - Strips both the comments and the attributes from the assembly and places them both in a separate LocFile.</span></span>  
  
4.  <span data-ttu-id="408b5-119">Když lokalizovatelný prostředky se extrahují z [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], atributy lokalizovatelnost dodržovaly [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] lokalizace rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="408b5-119">When localizable resources are extracted from [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], the localizability attributes are respected by the [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] Localization API.</span></span>  
  
5.  <span data-ttu-id="408b5-120">Lokalizační soubory komentář, obsahuje pouze vlastní poznámky, jsou součástí procesu lokalizace později.</span><span class="sxs-lookup"><span data-stu-id="408b5-120">Localization comment files, containing only free-form comments, are incorporated into the localization process at a later time.</span></span>  
  
 <span data-ttu-id="408b5-121">Následující příklad ukazuje, jak přidat lokalizace komentáře [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] souboru.</span><span class="sxs-lookup"><span data-stu-id="408b5-121">The following example shows how to add localization comments to a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file.</span></span>  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 <span data-ttu-id="408b5-122">V předchozí ukázce Localization.Attributes oddíl obsahuje atributů lokalizace a komentáře Localization.Comments části vlastní.</span><span class="sxs-lookup"><span data-stu-id="408b5-122">In the previous sample the Localization.Attributes section contains the localization attributes and the Localization.Comments section the free-form comments.</span></span> <span data-ttu-id="408b5-123">Následující tabulky ukazují na lokalizátora atributy a komentářů a jejich význam.</span><span class="sxs-lookup"><span data-stu-id="408b5-123">The following tables show the attributes and comments and their meaning to the localizer.</span></span>  
  
|<span data-ttu-id="408b5-124">Lokalizace atributy</span><span class="sxs-lookup"><span data-stu-id="408b5-124">Localization attributes</span></span>|<span data-ttu-id="408b5-125">Význam</span><span class="sxs-lookup"><span data-stu-id="408b5-125">Meaning</span></span>|  
|-----------------------------|-------------|  
|<span data-ttu-id="408b5-126">$Content (unmodifiable čitelný Text)</span><span class="sxs-lookup"><span data-stu-id="408b5-126">$Content (Unmodifiable Readable Text)</span></span>|<span data-ttu-id="408b5-127">Obsah elementu TextBlock nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="408b5-127">Contents of the TextBlock element cannot be modified.</span></span> <span data-ttu-id="408b5-128">Překladatelům při lokalizaci nelze změnit, je slovo "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="408b5-128">Localizers cannot change the word "Microsoft".</span></span> <span data-ttu-id="408b5-129">Obsah je lokalizátora viditelné (parametr Readable).</span><span class="sxs-lookup"><span data-stu-id="408b5-129">The content is visible (Readable) to the localizer.</span></span> <span data-ttu-id="408b5-130">Kategorie obsahu je text.</span><span class="sxs-lookup"><span data-stu-id="408b5-130">The category of the content is text.</span></span>|  
|<span data-ttu-id="408b5-131">FontFamily (Unmodifiable čitelné)</span><span class="sxs-lookup"><span data-stu-id="408b5-131">FontFamily (Unmodifiable Readable)</span></span>|<span data-ttu-id="408b5-132">Nelze změnit vlastnost rodiny písem TextBlock elementu, ale se zobrazí lokalizátora.</span><span class="sxs-lookup"><span data-stu-id="408b5-132">The font family property of the TextBlock element cannot be changed but it is visible to the localizer.</span></span>|  
  
|<span data-ttu-id="408b5-133">Lokalizace vlastní komentáře</span><span class="sxs-lookup"><span data-stu-id="408b5-133">Localization free-form comments</span></span>|<span data-ttu-id="408b5-134">Význam</span><span class="sxs-lookup"><span data-stu-id="408b5-134">Meaning</span></span>|  
|--------------------------------------|-------------|  
|<span data-ttu-id="408b5-135">$Content (ochranná známka)</span><span class="sxs-lookup"><span data-stu-id="408b5-135">$Content (Trademark)</span></span>|<span data-ttu-id="408b5-136">Vytváření aplikací informuje lokalizátora, že je obsah v elementu TextBlock ochrannou známku.</span><span class="sxs-lookup"><span data-stu-id="408b5-136">The application author tells the localizer that the content in the TextBlock element is a trademark.</span></span>|  
|<span data-ttu-id="408b5-137">Velikost písma (velikost písma ochranná známka)</span><span class="sxs-lookup"><span data-stu-id="408b5-137">FontSize (Trademark font size)</span></span>|<span data-ttu-id="408b5-138">Vytváření aplikací označuje, že vlastnost velikost písma postupujte podle velikosti standardní ochranná známka.</span><span class="sxs-lookup"><span data-stu-id="408b5-138">The application author indicates that the font size property should follow the standard trademark size.</span></span>|  
  
### <a name="localizability-attributes"></a><span data-ttu-id="408b5-139">Atributy lokalizovatelnosti</span><span class="sxs-lookup"><span data-stu-id="408b5-139">Localizability Attributes</span></span>  
 <span data-ttu-id="408b5-140">Informace v Localization.Attributes obsahuje seznam dvojic: název cílové hodnoty a lokalizovatelnost přidružené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="408b5-140">The information in Localization.Attributes contains a list of pairs: the targeted value name and the associated localizability values.</span></span> <span data-ttu-id="408b5-141">Název cílové může být název vlastnosti nebo speciální $Content název.</span><span class="sxs-lookup"><span data-stu-id="408b5-141">The target name can be a property name or the special $Content name.</span></span> <span data-ttu-id="408b5-142">Pokud je název vlastnosti, cílová hodnota je hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="408b5-142">If it is a property name, the targeted value is the value of the property.</span></span> <span data-ttu-id="408b5-143">Pokud je $Content, cílová hodnota je obsah elementu.</span><span class="sxs-lookup"><span data-stu-id="408b5-143">If it is $Content, the target value is the content of the element.</span></span>  
  
 <span data-ttu-id="408b5-144">Existují tři typy atributů:</span><span class="sxs-lookup"><span data-stu-id="408b5-144">There are three types of attributes:</span></span>  
  
-   <span data-ttu-id="408b5-145">**Kategorie**.</span><span class="sxs-lookup"><span data-stu-id="408b5-145">**Category**.</span></span> <span data-ttu-id="408b5-146">Určuje, zda má být upravitelnými z nástroje lokalizátora hodnotu.</span><span class="sxs-lookup"><span data-stu-id="408b5-146">This specifies whether a value should be modifiable from a localizer tool.</span></span> <span data-ttu-id="408b5-147">V tématu <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span><span class="sxs-lookup"><span data-stu-id="408b5-147">See <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span></span>  
  
-   <span data-ttu-id="408b5-148">**Čitelnost**.</span><span class="sxs-lookup"><span data-stu-id="408b5-148">**Readability**.</span></span> <span data-ttu-id="408b5-149">Určuje, zda má nástroj lokalizátora čtení (a zobrazení) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="408b5-149">This specifies whether a localizer tool should read (and display) a value.</span></span> <span data-ttu-id="408b5-150">V tématu <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span><span class="sxs-lookup"><span data-stu-id="408b5-150">See <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span></span>  
  
-   <span data-ttu-id="408b5-151">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="408b5-151">**Modifiability**.</span></span> <span data-ttu-id="408b5-152">Určuje, zda nástroj lokalizátora umožňuje hodnota má být změněn.</span><span class="sxs-lookup"><span data-stu-id="408b5-152">This specifies whether a localizer tool allows a value to be modified.</span></span> <span data-ttu-id="408b5-153">V tématu <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span><span class="sxs-lookup"><span data-stu-id="408b5-153">See <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span></span>  
  
 <span data-ttu-id="408b5-154">Tyto atributy lze zadat v libovolném pořadí oddělené mezerou.</span><span class="sxs-lookup"><span data-stu-id="408b5-154">These attributes can be specified in any order delimited by a space.</span></span> <span data-ttu-id="408b5-155">V případě, že jsou zadány duplicitní atributy, přepíše poslední atribut bývalé ty.</span><span class="sxs-lookup"><span data-stu-id="408b5-155">In case duplicate attributes are specified, the last attribute will override former ones.</span></span> <span data-ttu-id="408b5-156">Například Localization.Attributes = "Unmodifiable upravitelnými" sady Modifiability k Modifiable, protože se jedná o poslední hodnotu.</span><span class="sxs-lookup"><span data-stu-id="408b5-156">For example, Localization.Attributes = "Unmodifiable Modifiable" sets Modifiability to Modifiable because it is the last value.</span></span>  
  
 <span data-ttu-id="408b5-157">Modifiability a přehlednosti je zřejmých.</span><span class="sxs-lookup"><span data-stu-id="408b5-157">Modifiability and Readability are self-explanatory.</span></span> <span data-ttu-id="408b5-158">Atribut kategorie poskytuje předdefinovaných kategorií, které pomáhají lokalizátora při překladu textu.</span><span class="sxs-lookup"><span data-stu-id="408b5-158">The Category attribute provides predefined categories that help the localizer when translating text.</span></span> <span data-ttu-id="408b5-159">Kategorie, jako je Text, Label a název udělení lokalizátora informace o tom, jak převede text.</span><span class="sxs-lookup"><span data-stu-id="408b5-159">Categories, such as, Text, Label, and Title give the localizer information about how to translate the text.</span></span> <span data-ttu-id="408b5-160">Existují také speciální kategorie: None, zděděné, ignorovat a NeverLocalize.</span><span class="sxs-lookup"><span data-stu-id="408b5-160">There are also special categories: None, Inherit, Ignore, and NeverLocalize.</span></span>  
  
 <span data-ttu-id="408b5-161">V následující tabulce jsou uvedeny význam speciální kategorie.</span><span class="sxs-lookup"><span data-stu-id="408b5-161">The following table shows the meaning of the special categories.</span></span>  
  
|<span data-ttu-id="408b5-162">Kategorie</span><span class="sxs-lookup"><span data-stu-id="408b5-162">Category</span></span>|<span data-ttu-id="408b5-163">Význam</span><span class="sxs-lookup"><span data-stu-id="408b5-163">Meaning</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="408b5-164">Žádné</span><span class="sxs-lookup"><span data-stu-id="408b5-164">None</span></span>|<span data-ttu-id="408b5-165">Cílová hodnota nemá žádné definované kategorie.</span><span class="sxs-lookup"><span data-stu-id="408b5-165">Targeted value has no defined category.</span></span>|  
|<span data-ttu-id="408b5-166">Dědění</span><span class="sxs-lookup"><span data-stu-id="408b5-166">Inherit</span></span>|<span data-ttu-id="408b5-167">Cílová hodnota dědí z nadřazeného jeho kategorie.</span><span class="sxs-lookup"><span data-stu-id="408b5-167">Targeted value inherits its category from its parent.</span></span>|  
|<span data-ttu-id="408b5-168">Ignorovat</span><span class="sxs-lookup"><span data-stu-id="408b5-168">Ignore</span></span>|<span data-ttu-id="408b5-169">Cílová hodnota je ignorován v procesu lokalizace.</span><span class="sxs-lookup"><span data-stu-id="408b5-169">Targeted value is ignored in the localization process.</span></span> <span data-ttu-id="408b5-170">Ignorovat ovlivní pouze aktuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="408b5-170">Ignore affects only the current value.</span></span> <span data-ttu-id="408b5-171">Nebude to mít vliv podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="408b5-171">It will not affect child nodes.</span></span>|  
|<span data-ttu-id="408b5-172">NeverLocalize</span><span class="sxs-lookup"><span data-stu-id="408b5-172">NeverLocalize</span></span>|<span data-ttu-id="408b5-173">Aktuální hodnota nelze lokalizovat.</span><span class="sxs-lookup"><span data-stu-id="408b5-173">Current value cannot be localized.</span></span> <span data-ttu-id="408b5-174">Tuto kategorii zdědí podřízené objekty daného elementu.</span><span class="sxs-lookup"><span data-stu-id="408b5-174">This category is inherited by the children of an element.</span></span>|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a><span data-ttu-id="408b5-175">Lokalizace komentáře</span><span class="sxs-lookup"><span data-stu-id="408b5-175">Localization Comments</span></span>  
 <span data-ttu-id="408b5-176">Localization.Comments obsahuje řetězce volného formátu týkající se cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="408b5-176">Localization.Comments contains free-form strings concerning the targeted value.</span></span> <span data-ttu-id="408b5-177">Vývojáři aplikací můžete přidat informace, které poskytují překladatelům při lokalizaci pomocné parametry o tom, jak překladu textu aplikace.</span><span class="sxs-lookup"><span data-stu-id="408b5-177">Application developers can add information to give localizers hints about how the applications text should be translated.</span></span> <span data-ttu-id="408b5-178">Formát komentáře může být libovolný řetězec obklopená "(").</span><span class="sxs-lookup"><span data-stu-id="408b5-178">The format of the comments can be any string surrounded by "()".</span></span> <span data-ttu-id="408b5-179">Použití "\\, abyste se vyhnuli znaků.</span><span class="sxs-lookup"><span data-stu-id="408b5-179">Use '\\' to escape characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408b5-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="408b5-180">See Also</span></span>  
 [<span data-ttu-id="408b5-181">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="408b5-181">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="408b5-182">Vytvoření tlačítka pomocí automatického rozložení</span><span class="sxs-lookup"><span data-stu-id="408b5-182">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [<span data-ttu-id="408b5-183">Automatické rozložení použitím mřížky</span><span class="sxs-lookup"><span data-stu-id="408b5-183">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [<span data-ttu-id="408b5-184">Lokalizace aplikace</span><span class="sxs-lookup"><span data-stu-id="408b5-184">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
