---
title: Atributy a komentáře lokalizace
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7281ca6d76f0d2ffb5020feba236b4e4cf948bdd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141585"
---
# <a name="localization-attributes-and-comments"></a>Atributy a komentáře lokalizace
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]komentáře lokalizace jsou vlastnosti uvnitř zdrojového kódu XAML, které vývojáři poskytují pravidla a rady pro lokalizaci. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]komentáře lokalizace obsahují dvě sady informací: atributy lokalizovatelnosti a komentáře lokalizace volného tvaru. Lokalizovatelnost atributy jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používány rozhraní API lokalizace k označení, které prostředky mají být lokalizovány. Volné komentáře jsou všechny informace, které chce autor aplikace zahrnout.  

<a name="Localizer_Comments_"></a>
## <a name="localization-comments"></a>Komentáře k lokalizaci  
 Pokud autoři aplikace značky mají požadavky na určité prvky v XAML, jako jsou omezení délky textu, rodiny písem nebo velikosti písma, mohou tyto informace předat lokalizákům s komentáři v kódu XAML. Proces přidávání komentářů ke zdrojovému kódu je následující:  
  
1. Vývojář aplikace přidá komentáře lokalizace do zdrojového kódu XAML.  
  
2. Během procesu sestavení můžete v souboru .proj určit, zda mají být v sestavení ponechány komentáře lokalizace volného tvaru, odstraňte část komentářů nebo odstraňte všechny komentáře. Odstraněné komentáře jsou umístěny v samostatném souboru. Můžete zadat možnost `LocalizationDirectivesToLocFile` pomocí značky, např:You specify your option using a tag, eg:  
  
     `<LocalizationDirectivesToLocFile>`*hodnota*`</LocalizationDirectivesToLocFile>`  
  
3. Hodnoty, které lze přiřadit, jsou:  
  
    - **Žádné** – komentáře i atributy zůstávají uvnitř sestavení a není generován žádný samostatný soubor.  
  
    - **CommentsOnly** - Proužky pouze komentáře ze sestavení a umístí je do samostatnélocfile.  
  
    - **Všechny** - Proužky komentáře a atributy ze sestavy a umístí je oba v samostatnéLocFile.  
  
4. Při lokalizovatelné prostředky jsou extrahovány z BAML, atributy lokalizovatelnosti jsou respektovány BAML lokalizační rozhraní API.  
  
5. Soubory komentářů lokalizace, které obsahují pouze komentáře volného tvaru, jsou později začleněny do procesu lokalizace.  
  
 Následující příklad ukazuje, jak přidat komentáře lokalizace do souboru XAML.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 V předchozí ukázce obsahuje oddíl Localization.Attributes atributy lokalizace a oddíl Lokalizace.Komentáře volné komentáře. V následujících tabulkách jsou uvedeny atributy a komentáře a jejich význam pro lokalizátor.  
  
|Atributy lokalizace|Význam|  
|-----------------------------|-------------|  
|$Content (nemodifikovatelný čitelný text)|Obsah prvku TextBlock nelze změnit. Lokalizátory nemohou změnit slovo "Microsoft". Obsah je viditelný (čitelný) pro lokalizační systém. Kategorie obsahu je text.|  
|FontFamily (nemodifikovatelné čitelné)|Vlastnost font family elementu TextBlock nelze změnit, ale je viditelná pro lokalizátor.|  
  
|Lokalizace volných komentářů|Význam|  
|--------------------------------------|-------------|  
|$Content (ochranná známka)|Autor aplikace informuje lokalizátor, že obsah v Element TextBlock je ochranná známka.|  
|FontSize (velikost písma ochranné známky)|Autor aplikace označuje, že vlastnost velikosti písma by měla následovat standardní velikost ochranné známky.|  
  
### <a name="localizability-attributes"></a>Atributy lokalizovatelnosti  
 Informace v Localization.Attributes obsahuje seznam párů: název cílové hodnoty a přidružené hodnoty lokalizovatelnosti. Cílový název může být název vlastnosti nebo název zvláštní $Content. Pokud se jedná o název vlastnosti, cílová hodnota je hodnota vlastnosti. Pokud je $Content, cílová hodnota je obsah prvku.  
  
 Existují tři typy atributů:  
  
- **Kategorie**. Určuje, zda má být hodnota upravitelná z nástroje localizer. Viz třída <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Čitelnost**. Určuje, zda má nástroj pro lokalizační zařízení číst (a zobrazovat) hodnotu. Viz třída <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Modifikovatelnost**. Určuje, zda nástroj pro lokalizační systém umožňuje změnu hodnoty. Viz třída <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Tyto atributy lze zadat v libovolném pořadí odděleném mezerou. V případě, že jsou zadány duplicitní atributy, poslední atribut přepíše dřívější. Například Localization.Attributes = "Nemodifiable Modifikovatelné" nastaví modifikovatelnost modifikovatelné, protože je poslední hodnotu.  
  
 Modifikovatelnost a čitelnost jsou samozřejmé. Category Atribut poskytuje předdefinované kategorie, které pomáhají lokalizační prostředek při překladu textu. Kategorie, například Text, Popisek a Název poskytují localizer informace o tom, jak přeložit text. Existují také speciální kategorie: Žádné, Dědit, Ignorovat a NeverLocalize.  
  
 V následující tabulce je uveden význam zvláštních kategorií.  
  
|Kategorie|Význam|  
|--------------|-------------|  
|Žádný|Cílená hodnota nemá žádnou definovanou kategorii.|  
|Dědí|Cílová hodnota dědí svou kategorii z nadřazené položky.|  
|Ignorovat|Cílená hodnota je v procesu lokalizace ignorována. Ignorovat ovlivňuje pouze aktuální hodnotu. Neovlivní podřízené uzly.|  
|NeverLocalize|Aktuální hodnotu nelze lokalizovat. Tato kategorie je zděděna podřízenými objekty prvku.|  
  
<a name="Localization_Comments"></a>
## <a name="localization-comments"></a>Komentáře k lokalizaci  
 Lokalizace.Komentáře obsahuje řetězce volného tvaru týkající se cílové hodnoty. Vývojáři aplikací mohou přidat informace, které poskytují lokalizátory rady o tom, jak by měl být text aplikace přeložen. Formát komentáře může být libovolný řetězec obklopený "()". Pomocí\\znaku ' ' slouží k úniku znaků.  
  
## <a name="see-also"></a>Viz také

- [Globalizace pro WPF](globalization-for-wpf.md)
- [Vytvoření tlačítka pomocí automatického rozložení](how-to-use-automatic-layout-to-create-a-button.md)
- [Automatické rozložení pomocí mřížky](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalizace aplikace](how-to-localize-an-application.md)
