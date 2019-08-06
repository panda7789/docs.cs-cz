---
title: Zpracování prázdných znaků v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 077f19690d204d3b8f682d01c51feee9e9edbfd4
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796822"
---
# <a name="white-space-processing-in-xaml"></a>Zpracování prázdných znaků v jazyku XAML
Jazyková pravidla pro stav XAML, která významné prázdné znaky musí být zpracována [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementací procesoru. Toto téma obsahuje dokumentaci těchto pravidel jazyka XAML. Také dokumentuje další zpracování prázdných znaků, které je definováno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementací procesoru XAML a zapisovačem XAML pro serializaci.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definice prázdného místa  
 V souladu [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]s, prázdné znaky v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jsou mezery, odřádkování a tabulátor. Tyto [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] hodnoty odpovídají hodnotám 0020, 000a a 0009.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizace bílého prostoru  
 Ve výchozím nastavení dojde k následujícímu normálnímu vykonání [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] v případě, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] kdy procesor zpracovává soubor:  
  
1. Znaky odřádkování mezi východoasijskými znaky jsou odebrány. V části "východoasijské znaky" dále v tomto tématu najdete definice tohoto termínu.  
  
2. Všechny prázdné znaky (mezera, odřádkování, Tab) se převedou na mezery.  
  
3. Všechny po sobě jdoucí mezery se odstraní a nahradí o jednu mezeru.  
  
4. Místo, které následuje hned za počáteční značkou, se odstraní.  
  
5. Místo, které se bezprostředně před koncovou značkou odstraní.  
  
 "Výchozí" odpovídá stavu označenému výchozí hodnotou atributu [XML: Space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Prázdné znaky ve vnitřním textu a primitivních řetězcích  
 Předchozí normalizační pravidla platí pro vnitřní text, který je nalezen v rámci prvků XAML. Po normalizaci převede procesor XAML libovolný vnitřní text na odpovídající typ následujícím způsobem:  
  
- Pokud typ vlastnosti není kolekce, ale není přímo <xref:System.Object> typu, pokusí se procesor XAML převést na tento typ pomocí konvertoru typu. Neúspěšný převod tady způsobí chybu při kompilaci.  
  
- Pokud je typ vlastnosti kolekce a vnitřní text je souvislý (žádné zadané značky elementu), je vnitřní text analyzován jako jeden <xref:System.String>. Pokud typ kolekce nemůže přijmout <xref:System.String>, způsobí to také chybu při kompilaci.  
  
- Pokud je <xref:System.Object>typ vlastnosti, je vnitřní text analyzován jako jeden <xref:System.String>. V případě, že existují značky prvků, způsobí to chybu při kompilaci, protože <xref:System.Object> typ implikuje jeden objekt (<xref:System.String> nebo jinak).  
  
- Pokud je typ vlastnosti kolekce a vnitřní text není souvislý, první podřetězec je převeden na <xref:System.String> typ a přidán jako položka kolekce, přidaný prvek je přidán jako položka kolekce a nakonec koncový podřetězec (pokud existuje) je přidáno do kolekce jako třetí <xref:System.String> položka.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachování mezer  
 K dispozici je několik postupů pro zachování prázdných znaků ve [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zdroji pro případnou úpravu, která není [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ovlivněna normalizací prázdných prostorů procesoru.  
  
 **xml:space="preserve"** : Zadejte tento atribut na úrovni prvku, kde je požadováno zachování volného místa. Tím se zachová všechny prázdné znaky, což zahrnuje mezery, které mohou být přidány aplikacemi pro úpravu kódu do "poměrně tištěné" prvky pro zarovnání prvků jako vizuálně intuitivní vnořování. Bez ohledu na to, zda je vykreslení těchto prostorů určeno modelem obsahu pro element, který jej obsahuje. Vyhněte `xml:space="preserve"` se zadání na kořenové úrovni, protože většina modelů objektů nepovažuje prázdné znaky za významné bez ohledu na to, jak jste nastavili atribut. Globální `xml:space` nastavení může mít dopad na výkon při zpracování XAML (zejména serializace) v některých implementacích. Je vhodnější pouze nastavit atribut specificky na úrovni prvků, které vykreslují prázdné znaky v rámci řetězců, nebo jsou prázdné kolekce.  
  
 **Entity a nepevné mezery**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] podporuje umístění libovolné [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] entity v rámci textového objektového modelu. Můžete použít vyhrazené entity, jako je například nerozdělitelné místo (\#& 160; v kódování UTF-8). Lze také použít ovládací prvky formátovaného textu, které podporují znaky pro nerozdělení na místo. Měli byste být opatrní při použití entit pro simulaci vlastností rozložení, jako je například odsazení, protože výstup za běhu entit se bude lišit v závislosti na větším počtu faktorů, než by funkce pro vytváření odsazení vedlo k typickému systém rozložení, například správné použití panelů a okrajů. Například entity jsou mapovány na písma a mohou změnit velikost v reakci na výběr písem uživatele.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Východoasijské znaky  
 "Východoasijské znaky" jsou definovány jako množina [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] rozsahů znaků u + 20000 až u + 2FFFD a u + 30000 až u + 3FFFD. Tato podmnožina se také někdy označuje jako "znakové Symboly CJK". Další informace naleznete v tématu <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Prázdné znaky a modely textových obsahu  
 V praxi se zachováním prázdných znaků týká pouze podmnožiny všech možných modelů obsahu. Tato podmnožina se skládá z modelů obsahu, které mohou <xref:System.String> převzít typ singleton v některém formuláři <xref:System.String> , vyhrazené kolekci nebo kombinaci <xref:System.String> a jiné typy v <xref:System.Collections.IList> kolekci nebo <xref:System.Collections.Generic.ICollection%601> .  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Prázdné znaky a modely textových obsahu v subsystému WPF  
 Pro ilustraci zbytek tohoto oddílu odkazuje na konkrétní typy, které jsou definovány WPF. Funkce pro zpracování prázdných prostorů, které jsou popsány v tomto tématu, jsou obecně relevantní pro .NET Framework služby XAML i WPF. Chcete-li zobrazit toto chování v akci, můžete experimentovat s některými značkami jazyka XAML WPF, zobrazit výsledky v grafu objektů a poté znovu serializovat zpět na označení.  
  
 I pro modely obsahu, které mohou přijímat řetězce, je výchozím chováním v těchto modelech obsahu, že jakékoli prázdné znaky nejsou považovány za významné. Například <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListBoxItem>přebírá, ale prázdné znaky (například přeloženy mezi jednotlivými) nejsou zachovány a nejsou vykresleny. <xref:System.Collections.IList> Pokud se pokusíte použít přeloženy jako oddělovače mezi řetězci pro <xref:System.Windows.Controls.ListBoxItem> položky, nefunguje vůbec. řetězce, které jsou oddělené přeloženy, jsou považovány za jeden řetězec a jednu položku.  
  
 Tyto kolekce, které jsou zpracovávány prázdnými znaky jako významné, jsou obvykle součástí modelu flowového dokumentu. Primární kolekce, která podporuje chování uchovávání prázdných míst <xref:System.Windows.Documents.InlineCollection>, je. Tato třída kolekce je deklarována s <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>příponou. Pokud je tento atribut nalezen [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] , procesor bude v rámci kolekce považovat prázdné znaky za významné. Kombinace `xml:space="preserve"` a prázdných znaků <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> v rámci označené kolekce je, že všechny prázdné znaky jsou zachovány a vykresleny. Kombinace `xml:space="default"` a prázdných znaků <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> v rámci způsobí, že počáteční normalizovaná mezera popsaná výše, která opustí jednu mezeru v určitých pozicích, a tyto mezery se zachovají a vykreslí. To, jaké chování je žádoucí, je až vám, a pokud `xml:space` chcete povolit požadované chování, měli byste použít selektivně.  
  
 Některé vložené prvky, které označují LineBreak v modelu toku dokumentů, by také neměly vést k nadbytečnému prostoru, a to i v prázdné kolekci. Například <xref:System.Windows.Documents.LineBreak> element má stejný účel \<jako značka br/> ve formátu HTML a pro čitelnost <xref:System.Windows.Documents.LineBreak> v kódu, obvykle je oddělen od následného textu pomocí vytvořeného odřádkování. Tento řádek by neměl být normalizován na počáteční místo na následujícím řádku. Chcete-li toto chování povolit, definice třídy pro <xref:System.Windows.Documents.LineBreak> prvek <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>aplikuje třídu, která [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je následně interpretována procesorem, aby to znamenalo <xref:System.Windows.Documents.LineBreak> , že okolní prázdné znaky jsou vždy oříznuty.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Znakové entity XML a XAML](xml-character-entities-and-xaml.md)
- [XML: zpracování prostoru v jazyce XAML](xml-space-handling-in-xaml.md)
