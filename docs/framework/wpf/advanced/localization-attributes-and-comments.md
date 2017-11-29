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
ms.openlocfilehash: 5a603c854d389076d0054a43ebeb26f19145fa8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="localization-attributes-and-comments"></a>Atributy a komentáře lokalizace
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]lokalizace komentáře jsou vlastnosti, uvnitř [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód, poskytuje vývojářům poskytovat pravidly a tipy pro lokalizaci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]lokalizace komentáře obsahovat dvě sady informace: atributy lokalizovatelnost a lokalizace vlastní komentáře. Lokalizovatelnost atributy jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace rozhraní API k označení prostředků, které jsou lokalizovat. Vlastní komentáře jsou veškeré informace, které chce zahrnují vytváření aplikací.  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Lokalizace komentáře  
 Pokud kód aplikace autoři mít požadavky na konkrétní elementy v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], jako je například omezení délka textu, rodinu písem a velikost písma, se může nesou tyto informace k překladatelům při lokalizaci s komentáři v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kódu. Proces přidávání komentářů ke zdrojovému kódu vypadá takto:  
  
1.  Vývojář aplikace přidá lokalizace komentáře [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód.  
  
2.  Během procesu sestavení můžete určit, v souboru .proj zda psát komentáře volného formátu lokalizace v sestavení, pruhu se součástí komentáře nebo pruhu se všechny komentáře. Odstraní se na komentáře jsou umístěny v samostatném souboru. Zadejte vaše možnost použití `LocalizationDirectivesToLocFile` značka, např:  
  
     `<LocalizationDirectivesToLocFile>`*hodnotu*`</LocalizationDirectivesToLocFile>`  
  
3.  Hodnoty, které mohou být přiřazeny jsou:  
  
    -   **Žádný** – jak komentářů a atributů zůstane uvnitř sestavení a je generována žádný samostatný soubor.  
  
    -   **CommentsOnly** – odstraní pouze komentáře od sestavení a umístí je do samostatné LocFile.  
  
    -   **Všechny** – odstraní komentářů a atributů ze sestavení a umístí je i v samostatných LocFile.  
  
4.  Když lokalizovatelný prostředky se extrahují z [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], atributy lokalizovatelnost dodržovaly [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] lokalizace rozhraní API.  
  
5.  Lokalizační soubory komentář, obsahuje pouze vlastní poznámky, jsou součástí procesu lokalizace později.  
  
 Následující příklad ukazuje, jak přidat lokalizace komentáře [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] souboru.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 V předchozí ukázce Localization.Attributes oddíl obsahuje atributů lokalizace a komentáře Localization.Comments části vlastní. Následující tabulky ukazují na lokalizátora atributy a komentářů a jejich význam.  
  
|Lokalizace atributy|Význam|  
|-----------------------------|-------------|  
|$Content (unmodifiable čitelný Text)|Obsah elementu TextBlock nemůže být upraven. Překladatelům při lokalizaci nelze změnit, je slovo "Microsoft". Obsah je lokalizátora viditelné (parametr Readable). Kategorie obsahu je text.|  
|FontFamily (Unmodifiable čitelné)|Nelze změnit vlastnost rodiny písem TextBlock elementu, ale se zobrazí lokalizátora.|  
  
|Lokalizace vlastní komentáře|Význam|  
|--------------------------------------|-------------|  
|$Content (ochranná známka)|Vytváření aplikací informuje lokalizátora, že je obsah v elementu TextBlock ochrannou známku.|  
|Velikost písma (velikost písma ochranná známka)|Vytváření aplikací označuje, že vlastnost velikost písma postupujte podle velikosti standardní ochranná známka.|  
  
### <a name="localizability-attributes"></a>Atributy lokalizovatelnosti  
 Informace v Localization.Attributes obsahuje seznam dvojic: název cílové hodnoty a lokalizovatelnost přidružené hodnoty. Název cílové může být název vlastnosti nebo speciální $Content název. Pokud je název vlastnosti, cílová hodnota je hodnota vlastnosti. Pokud je $Content, cílová hodnota je obsah elementu.  
  
 Existují tři typy atributů:  
  
-   **Kategorie**. Určuje, zda má být upravitelnými z nástroje lokalizátora hodnotu. V tématu <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Čitelnost**. Určuje, zda má nástroj lokalizátora čtení (a zobrazení) hodnotu. V tématu <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability**. Určuje, zda nástroj lokalizátora umožňuje hodnota má být změněn. V tématu <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Tyto atributy lze zadat v libovolném pořadí oddělené mezerou. V případě, že jsou zadány duplicitní atributy, přepíše poslední atribut bývalé ty. Například Localization.Attributes = "Unmodifiable upravitelnými" sady Modifiability k Modifiable, protože se jedná o poslední hodnotu.  
  
 Modifiability a přehlednosti je zřejmých. Atribut kategorie poskytuje předdefinovaných kategorií, které pomáhají lokalizátora při překladu textu. Kategorie, jako je Text, Label a název udělení lokalizátora informace o tom, jak převede text. Existují také speciální kategorie: None, zděděné, ignorovat a NeverLocalize.  
  
 V následující tabulce jsou uvedeny význam speciální kategorie.  
  
|Kategorie|Význam|  
|--------------|-------------|  
|Žádné|Cílová hodnota nemá žádné definované kategorie.|  
|Dědění|Cílová hodnota dědí z nadřazeného jeho kategorie.|  
|Ignorovat|Cílová hodnota je ignorován v procesu lokalizace. Ignorovat ovlivní pouze aktuální hodnotu. Nebude to mít vliv podřízené uzly.|  
|NeverLocalize|Aktuální hodnota nelze lokalizovat. Tuto kategorii zdědí podřízené objekty daného elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Lokalizace komentáře  
 Localization.Comments obsahuje řetězce volného formátu týkající se cílové hodnoty. Vývojáři aplikací můžete přidat informace, které poskytují překladatelům při lokalizaci pomocné parametry o tom, jak překladu textu aplikace. Formát komentáře může být libovolný řetězec obklopená "("). Použití "\\, abyste se vyhnuli znaků.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro grafický subsystém WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Použití automatického rozložení pro vytvoření tlačítka](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Pomocí automatického rozložení mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [Lokalizace aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
