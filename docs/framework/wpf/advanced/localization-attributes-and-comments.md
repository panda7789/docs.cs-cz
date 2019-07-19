---
title: Atributy a komentáře lokalizace
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 1ef18802ab3568df00e29eb4ccaf717f4bdf4863
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330992"
---
# <a name="localization-attributes-and-comments"></a>Atributy a komentáře lokalizace
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]komentáře lokalizace jsou vlastnosti, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] uvnitř zdrojového kódu, dodávané vývojáři, aby poskytovali pravidla a pomocný parametr pro lokalizaci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]lokalizační Komentáře obsahují dvě sady informací: atributy lokalizovatelnosti a komentáře k lokalizaci volného formátu. Atributy lokalizovatelnosti používá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API pro lokalizaci k označení, které prostředky se mají lokalizovat. Komentáře k bezplatným formám obsahují informace, které autor aplikace chce zahrnout.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Komentáře lokalizace  
 Pokud autoři aplikace značky mají požadavky na konkrétní prvky v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], jako například omezení délky textu, rodina písem nebo velikost písma, mohou tyto informace sdělit lokalizovatelným s komentáři [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] v kódu. Postup přidávání komentářů do zdrojového kódu je následující:  
  
1. Vývojář aplikace přidá do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojového kódu komentáře lokalizace.  
  
2. Během procesu sestavení lze v souboru. proj zadat, zda mají být v sestavení ponechány komentáře k lokalizaci volného tvaru, oddělit část komentářů nebo vydělit všechny komentáře. Komentáře k odkladu jsou umístěné v samostatném souboru. Tuto možnost můžete zadat pomocí `LocalizationDirectivesToLocFile` značky, např.:  
  
     `<LocalizationDirectivesToLocFile>`*hodnota*`</LocalizationDirectivesToLocFile>`  
  
3. Hodnoty, které lze přiřadit:  
  
    - **Žádné** – komentáře a atributy zůstávají uvnitř sestavení a nejsou vygenerovány žádné samostatné soubory.  
  
    - **CommentsOnly** – odstraní pouze komentáře ze sestavení a umístí je do samostatného LocFile.  
  
    - **Vše** odstraní komentáře a atributy ze sestavení a umístí je do samostatného LocFile.  
  
4. Při extrakci lokalizovatelných prostředků z identifikátoru BAML jsou atributy lokalizovatelnosti respektovány rozhraním API lokalizace.  
  
5. Lokalizační soubory s komentáři obsahující pouze volné komentáře jsou začleněny do procesu lokalizace v pozdějším čase.  
  
 Následující příklad ukazuje, jak přidat lokalizační komentáře do [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] souboru.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 V předchozím příkladu obsahuje oddíl lokalizace. Attributes atributy lokalizace a oddíl Localization. Comments s poznámkami k volnému formátu. V následujících tabulkách jsou uvedeny atributy a komentáře a jejich význam pro lokalizátora.  
  
|Atributy lokalizace|Význam|  
|-----------------------------|-------------|  
|$Content (neupravitelný text s možností čtení)|Obsah elementu TextBlock nelze upravovat. Nemůžou změnit slovo Microsoft. Obsah je viditelný (čitelný) do lokalizátora. Kategorie obsahu je text.|  
|FontFamily (neupravitelný čitelný)|Vlastnost rodina písma prvku TextBlock se nedá změnit, ale je viditelná pro lokalizátora.|  
  
|Lokalizace komentářů volných součástí|Význam|  
|--------------------------------------|-------------|  
|$Content (ochranná známka)|Autor aplikace informuje lokalizátora o tom, že obsah v prvku TextBlock je ochranná známka.|  
|FontSize (velikost písma ochranné známky)|Autor aplikace indikuje, že vlastnost velikost písma by měla dodržovat standardní velikost ochranné známky.|  
  
### <a name="localizability-attributes"></a>Atributy lokalizovatelnosti  
 Informace v lokalizaci. atributy obsahují seznam párů: cílový název hodnoty a související hodnoty lokalizovatelnosti. Název cíle může být název vlastnosti nebo speciální $Content název. Pokud se jedná o název vlastnosti, cílová hodnota je hodnota vlastnosti. Pokud je $Content, je cílovou hodnotou obsah elementu.  
  
 Existují tři typy atributů:  
  
- **Kategorie**. Určuje, zda má být hodnota upravitelná z nástroje lokalizátora Tool. Viz <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Čitelnost**. Určuje, zda má nástroj lokalizátora číst (a zobrazit) hodnotu. Viz <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Upravitelnost**. Určuje, zda nástroj lokalizátora umožňuje úpravu hodnoty. Viz <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Tyto atributy lze zadat v libovolném pořadí odděleném mezerou. V případě, že jsou zadány duplicitní atributy, nahradí poslední atribut původní atribut. Například lokalizace. Attributes = "unupravitelně upravitelná" nastavuje možnost upravitelnosti, protože se jedná o poslední hodnotu.  
  
 Čitelnost a čitelnost jsou samozřejmé. Atribut Category poskytuje předdefinované kategorie, které pomůžou lokalizátora při překladu textu. Kategorie, jako je například text, popisek a název, poskytují lokalizátora informace o tom, jak překládat text. K dispozici jsou také speciální kategorie: Žádná, zdědit, ignorovat a NeverLocalize.  
  
 V následující tabulce je uveden význam speciálních kategorií.  
  
|Kategorie|Význam|  
|--------------|-------------|  
|Žádné|Cílová hodnota nemá žádnou definovanou kategorii.|  
|Přenesení|Cílová hodnota zdědí svoji kategorii od jejího nadřazeného prvku.|  
|Ignorovat|Cílová hodnota se v procesu lokalizace ignoruje. Hodnota ignorovat má vliv pouze na aktuální hodnotu. Nebude to mít vliv na podřízené uzly.|  
|NeverLocalize|Aktuální hodnotu nelze lokalizovat. Tato kategorie je zděděna podřízenými objekty elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Komentáře lokalizace  
 Lokalizace. Komentáře obsahují řetězce volného formátu týkající se cílové hodnoty. Vývojáři aplikací můžou přidat informace, které podávají pokynům pro lokalizaci o tom, jak by měl být text aplikací přeložen. Formát komentáře může být libovolný řetězec, který je ohraničen znakem "()". Pro řídicí\\znaky použijte ' '.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Vytvoření tlačítka pomocí automatického rozložení](how-to-use-automatic-layout-to-create-a-button.md)
- [Automatické rozložení použitím mřížky](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizace aplikace](how-to-localize-an-application.md)
