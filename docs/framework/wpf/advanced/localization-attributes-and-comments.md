---
title: Atributy a komentáře lokalizace
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4e4c4891a905a5e4458ad5fc21a512c1dfe6f74e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092913"
---
# <a name="localization-attributes-and-comments"></a>Atributy a komentáře lokalizace
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] komentáře lokalizace jsou vlastnosti, uvnitř [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód, získáte ho od vývojářům poskytuje pravidla a pokyny pro lokalizaci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] lokalizace komentáře obsahují dvě sady informace: lokalizovatelnosti atributy a komentáře lokalizace volného tvaru. Lokalizovatelnost atributy jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] lokalizace rozhraní API k označení prostředků, které mají být lokalizována. Komentáře volného tvaru jsou veškeré informace, které autor aplikace chce zahrnovat.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Komentáře lokalizace  
 Pokud kód aplikace Autoři mají požadavky na konkrétní prvky v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], jako je například omezení na délku textu rodinu písem a velikost písma sdělují Lokalizátoři s komentáři v těchto informací [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kódu. Proces pro přidávání komentářů ke zdrojovému kódu vypadá takto:  
  
1.  Vývojář aplikace přidá komentáře lokalizace [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] zdrojový kód.  
  
2.  Během procesu sestavení můžete určit v souboru souborů .proj, jestli se má zanechávat komentáře lokalizace volného tvaru v sestavení, pásků si část poznámky nebo pruhu si všechny komentáře. Komentáře odebrána navýšením kapacity jsou umístěné v samostatném souboru. Zadejte vaše možnost použití `LocalizationDirectivesToLocFile` značku, třeba:  
  
     `<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`  
  
3.  Je možné přiřadit hodnoty jsou:  
  
    -   **Žádný** – jak komentářů a atributů zůstávají uvnitř sestavení a vygeneruje se žádný samostatný soubor.  
  
    -   **CommentsOnly** – odebere jenom komentářů ze sestavení a umístí je do samostatné LocFile.  
  
    -   **Všechny** – odstraní komentářů a atributů ze sestavení a umístí je do samostatné LocFile.  
  
4.  Když lokalizovatelné prostředky se extrahují z [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], jsou dodržovány lokalizovatelnosti atributy [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] lokalizace rozhraní API.  
  
5.  Soubory komentáře lokalizace, obsahující pouze volného tvaru komentáře, jsou začleněny do proces lokalizace později.  
  
 Následující příklad ukazuje, jak přidat komentáře lokalizace [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] souboru.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 V předchozí ukázce Localization.Attributes oddíl obsahuje lokalizace atributy a komentáře Localization.Comments části volného tvaru. Následující tabulky popisují atributy a komentáře a jejich význam pro lokalizátora.  
  
|Lokalizace atributy|Význam|  
|-----------------------------|-------------|  
|$Content (neupravitelných čitelný Text)|Obsah prvku TextBlock nelze upravit. Lokalizátoři nelze změní celé slovo "Microsoft". Obsah je lokalizátora viditelné (přístupné pro čtení). Kategorie obsahu je text.|  
|FontFamily (neupravitelných čitelné)|Nelze změnit vlastnost rodiny písem prvku TextBlock, ale je viditelný lokalizátora.|  
  
|Komentáře lokalizace volného tvaru|Význam|  
|--------------------------------------|-------------|  
|$Content (Trademark)|Vytváření aplikací říká lokalizátora, že obsah prvku TextBlock je ochranná známka.|  
|Velikost písma (ochranná známka písmo)|Autor aplikace znamená, že vlastnost velikost písma by měly dodržovat standardní ochranná známka velikost.|  
  
### <a name="localizability-attributes"></a>Atributy lokalizovatelnosti  
 Informace v Localization.Attributes obsahuje seznam dvojic, přičemž: název cílové hodnoty a lokalizovatelnosti přidružené hodnoty. Název cílové může být název vlastnosti nebo speciální $Content název. Pokud je název vlastnosti, cílová hodnota je hodnota vlastnosti. Pokud je $Content, cílová hodnota je obsah elementu.  
  
 Existují tři typy atributů:  
  
-   **Kategorie**. Určuje, zda má být hodnota z nástroje lokalizátora lze měnit. Viz <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Lepší čitelnost**. Určuje, zda by měl nástroj lokalizátora čtení (a zobrazení) hodnotu. Viz <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability**. Určuje, zda nástroj lokalizátora umožňuje hodnota má být upraven. Viz <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Tyto atributy můžete zadat v libovolném pořadí oddělené mezerou. V případě, že jsou zadány duplicitní atributy, přepíše atribut posledních ty dřívější. Například Localization.Attributes = "Neupravitelných upravitelná" Nastaví Modifiability k Modifiable, protože se jedná o poslední hodnotu.  
  
 Modifiability a čitelnost není potřeba vysvětlovat. Kategorie atributu poskytuje předdefinované kategorie, které pomáhají lokalizátora při překladu textu. Kategorie, jako jsou například Text, popisek a název dávající lokalizátora informace o tom, jak převést text. Existují také speciální kategorie: NONE, dědění, ignorovat a NeverLocalize.  
  
 V následující tabulce jsou uvedeny význam zvláštních kategoriích.  
  
|Kategorie|Význam|  
|--------------|-------------|  
|Žádný|Cílová hodnota nemá žádné definované kategorie.|  
|Dědění|Cílová hodnota dědí z nadřazeného jeho kategorie.|  
|Ignorovat|Cílová hodnota je ignorována v proces lokalizace. Ignorovat ovlivní pouze aktuální hodnotu. To nebude mít vliv na podřízené uzly.|  
|NeverLocalize|Aktuální hodnota nemůže být lokalizována. Tato kategorie dědí podřízené objekty daného elementu.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Komentáře lokalizace  
 Localization.Comments obsahuje týkající se cílová hodnota řetězce volného tvaru. Vývojáři aplikací mohou přidat informace, které poskytují Lokalizátoři nápovědu, jak by měl přeložit text žádosti. Formát komentářů může být libovolný řetězec ohraničený "()". Použití "\\" řídicí znaky.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Vytvoření tlačítka pomocí automatického rozložení](how-to-use-automatic-layout-to-create-a-button.md)
- [Automatické rozložení pomocí mřížky](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizace aplikace](how-to-localize-an-application.md)
