---
title: Zpracování prázdných znaků v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: bf5c13f59b9e9c4774fde952a52289abb2815b65
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395985"
---
# <a name="white-space-processing-in-xaml"></a>Zpracování prázdných znaků v jazyku XAML
Jazyková pravidla pro stav XAML, která významné prázdné znaky musí být zpracována implementací procesoru [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]. Toto téma obsahuje dokumentaci těchto pravidel jazyka XAML. Také dokumentuje další zpracování prázdných znaků, které je definováno implementací procesoru XAML [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a zapisovačem XAML pro serializaci.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definice prázdného místa  
 V souladu s [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)] prázdné znaky v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jsou mezery, odřádkování a karta. Tyto hodnoty odpovídají hodnotám Unicode 0020, 000A a 0009.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizace bílého prostoru  
 Ve výchozím nastavení dojde k následujícímu normálnímu odkladu v případě, že procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracovává soubor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]:  
  
1. Znaky odřádkování mezi východoasijskými znaky jsou odebrány. V části "východoasijské znaky" dále v tomto tématu najdete definice tohoto termínu.  
  
2. Všechny prázdné znaky (mezera, odřádkování, Tab) se převedou na mezery.  
  
3. Všechny po sobě jdoucí mezery se odstraní a nahradí o jednu mezeru.  
  
4. Místo, které následuje hned za počáteční značkou, se odstraní.  
  
5. Místo, které se bezprostředně před koncovou značkou odstraní.  
  
 "Výchozí" odpovídá stavu označenému výchozí hodnotou atributu [XML: Space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Prázdné znaky ve vnitřním textu a primitivních řetězcích  
 Předchozí normalizační pravidla platí pro vnitřní text, který je nalezen v rámci prvků XAML. Po normalizaci převede procesor XAML libovolný vnitřní text na odpovídající typ následujícím způsobem:  
  
- Pokud typ vlastnosti není kolekce, ale není přímo typu <xref:System.Object>, pokusí se procesor XAML převést na tento typ pomocí konvertoru typu. Neúspěšný převod tady způsobí chybu při kompilaci.  
  
- Pokud je typ vlastnosti kolekce a vnitřní text je souvislý (žádné zadané značky elementu), je vnitřní text analyzován jako jeden <xref:System.String>. Pokud typ kolekce nemůže přijmout <xref:System.String>, tím dojde také k chybě při kompilaci.  
  
- Pokud je typ vlastnosti <xref:System.Object>, je vnitřní text analyzován jako jediný <xref:System.String>. V případě, že existují značky prvků, způsobí to chybu při kompilaci, protože typ <xref:System.Object> implikuje jeden objekt (<xref:System.String> nebo jinak).  
  
- Pokud je typ vlastnosti kolekce a vnitřní text není souvislý, první podřetězec je převeden na <xref:System.String> a přidán jako položka kolekce, přidaný prvek se přidá jako položka kolekce a nakonec se přidá koncová část řetězce (pokud existuje). do kolekce jako třetí položka <xref:System.String>.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachování mezer  
 K dispozici je několik postupů pro zachování prázdných znaků ve zdrojovém [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pro případ, že je neovlivněná normalizace [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesoru.  
  
 **XML: space = "preserve"** : Určete tento atribut na úrovni prvku, kde je požadováno zachování volného místa. Tím se zachová všechny prázdné znaky, což zahrnuje mezery, které mohou být přidány aplikacemi pro úpravu kódu do "poměrně tištěné" prvky pro zarovnání prvků jako vizuálně intuitivní vnořování. Bez ohledu na to, zda je vykreslení těchto prostorů určeno modelem obsahu pro element, který jej obsahuje. Vyhněte se zadání `xml:space="preserve"` na kořenové úrovni, protože většina modelů objektů nepovažuje prázdné znaky za významné bez ohledu na nastavení atributu. Nastavení `xml:space` globálně může mít vliv na zpracování XAML (zvláště serializace) v některých implementacích. Je vhodnější pouze nastavit atribut specificky na úrovni prvků, které vykreslují prázdné znaky v rámci řetězců, nebo jsou prázdné kolekce.  
  
 **Entity a nepevné mezery**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] podporuje umístění libovolné entity Unicode v rámci modelu textového objektu. Můžete použít vyhrazené entity, jako je například nerozdělitelné místo (& \#160; v kódování UTF-8). Lze také použít ovládací prvky formátovaného textu, které podporují znaky pro nerozdělení na místo. Měli byste být opatrní při použití entit pro simulaci vlastností rozložení, jako je například odsazení, protože výstup za běhu entit se bude lišit v závislosti na větším počtu faktorů, než by funkce pro vytváření odsazení vedlo k typickému systém rozložení, například správné použití panelů a okrajů. Například entity jsou mapovány na písma a mohou změnit velikost v reakci na výběr písem uživatele.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Východoasijské znaky  
 "Východoasijské znaky" jsou definovány jako sada rozsahů znaků Unicode U + 20000 až U + 2FFFD a U + 30000 až U + 3FFFD. Tato podmnožina se také někdy označuje jako "znakové Symboly CJK". Další informace najdete v tématu <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Prázdné znaky a modely textových obsahu  
 V praxi se zachováním prázdných znaků týká pouze podmnožiny všech možných modelů obsahu. Tato podmnožina se skládá z modelů obsahu, které mohou převzít typ singleton <xref:System.String> v některém formuláři, vyhrazené kolekci <xref:System.String> nebo ve směsi <xref:System.String> a jiné typy v kolekci <xref:System.Collections.IList> nebo <xref:System.Collections.Generic.ICollection%601>.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Prázdné znaky a modely textových obsahu v subsystému WPF  
 Pro ilustraci zbytek tohoto oddílu odkazuje na konkrétní typy, které jsou definovány WPF. Funkce pro zpracování prázdných prostorů, které jsou popsány v tomto tématu, jsou obecně relevantní pro .NET Framework služby XAML i WPF. Chcete-li zobrazit toto chování v akci, můžete experimentovat s některými značkami jazyka XAML WPF, zobrazit výsledky v grafu objektů a poté znovu serializovat zpět na označení.  
  
 I pro modely obsahu, které mohou přijímat řetězce, je výchozím chováním v těchto modelech obsahu, že jakékoli prázdné znaky nejsou považovány za významné. Například <xref:System.Windows.Controls.ListBox> přebírá <xref:System.Collections.IList>, ale prázdné místo (například přeloženy mezi jednotlivými <xref:System.Windows.Controls.ListBoxItem>) není zachováno a není vykresleno. Pokud se pokusíte použít přeloženy jako oddělovače mezi řetězci pro položky <xref:System.Windows.Controls.ListBoxItem>, nefunguje vůbec. řetězce, které jsou odděleny přeloženy, jsou považovány za jeden řetězec a jednu položku.  
  
 Tyto kolekce, které jsou zpracovávány prázdnými znaky jako významné, jsou obvykle součástí modelu flowového dokumentu. Primární kolekce, která podporuje chování při zachování prázdných míst, je <xref:System.Windows.Documents.InlineCollection>. Tato třída kolekce je deklarována s <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; Při nalezení tohoto atributu procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] bude v rámci kolekce považovat prázdné znaky za významné. Kombinace `xml:space="preserve"` a prázdných znaků v označené kolekci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> je, že všechny prázdné znaky jsou zachovány a vykresleny. Kombinace `xml:space="default"` a prázdných znaků v rámci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> způsobuje počáteční normalizovanou mezeru popsanou výše, která opustí jednu mezeru v určitých pozicích a tyto prostory se zachovají a vykreslí. To, jaké chování je žádoucí, je až vám, a pokud chcete požadované chování povolit, použijte `xml:space` selektivně.  
  
 Některé vložené prvky, které označují LineBreak v modelu toku dokumentů, by také neměly vést k nadbytečnému prostoru, a to i v prázdné kolekci. Například element <xref:System.Windows.Documents.LineBreak> má stejný účel jako značka \<BR/> ve formátu HTML a pro čitelnost v kódu, obvykle je <xref:System.Windows.Documents.LineBreak> oddělená od následného textu pomocí vytvořeného odřádkování. Tento řádek by neměl být normalizován na počáteční místo na následujícím řádku. Chcete-li toto chování povolit, definice třídy pro <xref:System.Windows.Documents.LineBreak> použije <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, který je následně interpretován procesorem [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], což znamená, že prázdné znaky okolní <xref:System.Windows.Documents.LineBreak> jsou vždy oříznuty.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Znakové entity XML a XAML](xml-character-entities-and-xaml.md)
- [XML: zpracování prostoru v jazyce XAML](xml-space-handling-in-xaml.md)
