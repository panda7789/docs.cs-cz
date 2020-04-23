---
title: Zpracování prázdných znaků v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071603"
---
# <a name="white-space-processing-in-xaml"></a>Zpracování prázdných znaků v jazyku XAML

Pravidla jazyka XAML uvádějí, že implementací procesoru [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] musí být zpracováno významné prázdné místo. Tento článek dokumentuje tato jazyková pravidla XAML. Dokumentuje také další zpracování prázdného místa, které je definováno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementací procesoru XAML a zapisovače XAML pro serializaci.

## <a name="white-space-definition"></a>Definice prázdného místa

V souladu s jazykem [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] XML jsou prázdné znaky mezery, linkový signál a karta. Tyto odpovídají hodnotám Unicode 0020, 000A a 0009.

## <a name="white-space-normalization"></a>Normalizace prázdného místa

Ve výchozím nastavení dochází k následující normalizaci mezer, když [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesor zpracuje [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] soubor:

1. Znaky linefeedu mezi východoasijskými znaky se odstraní. Definice tohoto termínu naleznete v části Východoasijské znaky dále v tomto tématu.

2. Všechny prázdné znaky (mezera, linkový posuv, karta) jsou převedeny na mezery.

3. Všechny po sobě jdoucí mezery jsou odstraněny a nahrazeny jednou mezerou.

4. Mezera bezprostředně za počáteční značkou bude odstraněna.

5. Mezera bezprostředně před odstraněním koncové značky.

"Výchozí" odpovídá stavu označenému výchozí hodnotou atributu [xml:space.](xml-space-handling.md)

## <a name="white-space-in-inner-text-and-string-primitives"></a>Prázdné místo ve vnitřním textu a základní řetězec

Předchozí pravidla normalizace platí pro vnitřní text, který se nachází v elementech XAML. Po normalizaci převede procesor XAML libovolný vnitřní text na příslušný typ následujícím způsobem:

- Pokud typ vlastnosti není kolekce, ale není <xref:System.Object> přímo typ, procesor XAML pokusí převést na tento typ pomocí jeho převaděč typu. Neúspěšný převod zde způsobí chybu v době kompilace.

- Pokud je typem vlastnosti kolekce a vnitřní text je souvislý (žádné značky zasahujících prvků), vnitřní text je analyzován jako jeden <xref:System.String>. Pokud typ kolekce <xref:System.String>nelze přijmout , to také způsobí chybu v době kompilace.

- Pokud je <xref:System.Object>typ vlastnosti , vnitřní text je analyzován <xref:System.String>jako jeden . Pokud existují zasahující element značky, to <xref:System.Object> způsobí chybu v<xref:System.String> době kompilace, protože typ znamená jeden objekt (nebo jinak).

- Pokud je typ vlastnosti kolekce a vnitřní text není souvislý, první podřetězec je převeden <xref:System.String> na a přidán jako položka kolekce, intervenující prvek je přidán jako položka kolekce a nakonec koncový podřetězec <xref:System.String> (pokud existuje) je přidán do kolekce jako třetí položka.

## <a name="preserving-white-space"></a>Zachování prázdného místa

Existuje několik technik pro zachování prázdné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] místo ve zdroji pro [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] případné prezentace, které nejsou ovlivněny normalizace prázdnémísto procesoru.

**xml:space="preserve"**: Zadejte tento atribut na úrovni prvku, kde je žádoucí zachování prázdného místa. Tím se zachová všechny prázdné znaky, které zahrnují mezery, které mohou být přidány aplikacemi pro úpravu kódu pro "pretty-print" zarovnání prvků jako vizuálně intuitivní vnoření. Však zda tyto mezery vykreslení je určena model obsahu pro obsahující prvek. Vyhněte `xml:space="preserve"` se určení na kořenové úrovni, protože většina objektových modelů nepovažuje prázdné místo za významné bez ohledu na to, jak atribut nastavíte. Globální `xml:space` nastavení může mít důsledky pro výkon zpracování XAML (zejména serializace) v některých implementacích. Je vhodnější nastavit atribut pouze na úrovni prvků, které vykreslují prázdné místo v rámci řetězce nebo jsou významné kolekce prázdné místo.

**Entity a nerozdělitelné mezery**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] podporuje umístění libovolné entity Unicode v textovém objektovém modelu. Můžete použít vyhrazené entity, jako je \#například nerozdělitelné místo (&160; v kódování UTF-8). Můžete také použít ovládací prvky s formátovaným textem, které podporují nerozdělitelné znaky mezery. Měli byste být opatrní, pokud používáte entity k simulaci charakteristik rozložení, jako je například odsazení, protože výstup za běhu entit se bude lišit v závislosti na větším počtu faktorů, než by schopnosti pro vytváření odsazení vedou k typickému systému rozložení, jako je správné použití panelů a okrajů. Entity jsou například mapovány na písma a mohou změnit velikost v reakci na výběr písma uživatele.

## <a name="east-asian-characters"></a>Východoasijské znaky

"Východoasijské znaky" jsou definovány jako sada rozsahů znaků Unicode U+20000 až U+2FFFD a U+30000 až U+3FFFD. Tato podmnožina je také někdy označována jako "CJK ideographs". Další informace naleznete v tématu <https://www.unicode.org>.

## <a name="white-space-and-text-content-models"></a>Prázdné a textové modely obsahu

V praxi je zachování prázdného místa pouze problémem pro podmnožinu všech možných modelů obsahu. Tato podmnožina se skládá z modelů <xref:System.String> obsahu, které mohou <xref:System.String> mít singleton <xref:System.String> typu v nějaké <xref:System.Collections.IList> <xref:System.Collections.Generic.ICollection%601> formě, vyhrazené kolekce nebo směs a jiné typy v nebo kolekce.

### <a name="white-space-and-text-content-models-in-wpf"></a>Prázdné a textové modely obsahu ve WPF

Pro ilustrační účely zbytek této části odkazuje na konkrétní typy, které jsou definovány WPF. Funkce zpracování prázdného místa, které jsou popsány v tomto článku jsou relevantní pro služby .NET XAML a WPF. Chcete-li zobrazit toto chování v akci, můžete experimentovat s některými značkami WPF XAML, zobrazit výsledky v grafu objektu a pak serializovat zpět na značky znovu.

I pro modely obsahu, které mohou trvat řetězce, výchozí chování v rámci těchto modelů obsahu je, že všechny prázdné místo, které zůstane není považován o významné. Například <xref:System.Windows.Controls.ListBox> trvá <xref:System.Collections.IList>, ale prázdné místo (například linefeeds mezi každým <xref:System.Windows.Controls.ListBoxItem>) není zachována a není vykreslen. Pokud se pokusíte použít linefeeds jako oddělovače mezi řetězci pro <xref:System.Windows.Controls.ListBoxItem> položky, nefunguje vůbec; řetězce, které jsou odděleny linefeeds jsou považovány za jeden řetězec a jednu položku.

Tyto kolekce, které považují prázdné místo za významné, jsou obvykle součástí modelu dokumentu toku. Primární kolekce, která podporuje chování <xref:System.Windows.Documents.InlineCollection>zachování prázdnémísto je . Tato třída kolekce je <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>deklarována s ; Pokud je tento atribut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] nalezen, procesor bude považovat prázdné místo v rámci kolekce jako významné. Kombinace `xml:space="preserve"` a prázdné místo <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> v rámci označené kolekce je, že všechny prázdné místo je zachována a vykreslena. Kombinace `xml:space="default"` a prázdné místo <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> v rámci způsobí počáteční white-space normalizace popsané dříve, což ponechává jednu mezeru v určitých pozicích a tyto mezery jsou zachovány a vykresleny. Chování, které chování je žádoucí, je `xml:space` na vás a měli byste použít selektivně povolit chování, které chcete.

Také některé včleněné prvky, které connote konec řádku v modelu dokumentu toku by záměrně neměla zavést další mezeru i v kolekci významné prázdné místo. Například <xref:System.Windows.Documents.LineBreak> prvek má stejný účel \<jako značka BR/> v HTML a pro čitelnost <xref:System.Windows.Documents.LineBreak> ve značkách je obvykle a oddělena od jakéhokoli následného textu vytvořeným linkovým kanálem. Tento linefeed by neměl být normalizován, aby se stal úvodním prostorem v následujícím řádku. Chcete-li povolit toto <xref:System.Windows.Documents.LineBreak> chování, definice <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>třídy pro prvek [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] použije , který je <xref:System.Windows.Documents.LineBreak> pak interpretován procesorem znamenat, že prázdné místo okolí je vždy oříznut.

## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../fundamentals/xaml.md)
- [Entity znaků XML a XAML](xml-character-entities.md)
- [xml:zpracování prostoru v XAML](xml-space-handling.md)
