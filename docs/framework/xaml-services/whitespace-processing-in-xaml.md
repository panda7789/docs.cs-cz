---
title: Zpracování mezerových znaků v XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 89f8a4675b3edc23913549bc24f0d9ae16917519
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45595058"
---
# <a name="white-space-processing-in-xaml"></a>Zpracování mezerových znaků v XAML
Stav jazykových pravidel pro XAML, že významné mezery, musí být zpracovány [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru. Toto téma popisuje tato pravidla jazyka XAML. Také dokumenty prázdných další zpracování, který je definován [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] provádění procesoru XAML a XAML zapisovače pro serializaci.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definice prázdné znaky  
 Konzistentní s [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], prázdných znaků v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jsou místa, odřádkování a karty. Tyto weby odpovídají [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] hodnoty 0020 000A a 0009 v uvedeném pořadí.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizace prázdné znaky  
 Ve výchozím nastavení dojde k následujícím normalizace prázdných při [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesů procesoru [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] souboru:  
  
1.  Znaky odřádkování mezi východoasijské znaky jsou odebrány. V části "Východoasijské znaky" dále v tomto tématu pro definici tento termín.  
  
2.  Všechny prázdné znaky (místo, odřádkování, karta) budou převedeny na mezery.  
  
3.  Všechny po sobě následující mezery jsou odstraněna a nahrazuje jednu mezeru.  
  
4.  Místo ihned po počáteční značce se odstraní.  
  
5.  Odstraní se místo těsně před koncovou značku.  
  
 "Výchozí" odpovídá stavu udávají výchozí hodnota [XML: Space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) atribut.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Prázdný znak ve vnitřním textu a řetězce primitiv  
 Předchozí normalizace pravidla se vztahují na vnitřní text, který se nachází v rámci elementů XAML. Po normalizace procesor XAML převede všechny vnitřní text do příslušného typu následujícím způsobem:  
  
-   Pokud typ vlastnosti není kolekce, ale není přímo <xref:System.Object> typ procesoru XAML pokusí převést na daný typ pomocí jeho typ převaděče. Selhal převod způsobí chybu kompilace.  
  
-   Pokud typ vlastnosti je kolekce a vnitřní text je souvislý (žádná síťová značky elementů), vnitřní text analyzován jako jediný <xref:System.String>. Pokud typ kolekce nelze přijmout <xref:System.String>, to také způsobí chybu kompilace.  
  
-   Pokud je typ proměnné <xref:System.Object>, vnitřní text analyzován jako jediný <xref:System.String>. Pokud existuje jsou intervenující značky elementů, to způsobí chybu kompilace, protože <xref:System.Object> typ znamená jeden objekt (<xref:System.String> nebo jinak).  
  
-   Pokud typ vlastnosti je kolekce a vnitřní text není souvislé, prvního podřetězce je převeden do <xref:System.String> a přidány jako položky kolekce, použité prvek je přidán jako kolekce položek, a nakonec koncové dílčí řetězec (pokud existuje) je Přidat do kolekce jako třetí <xref:System.String> položky.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachování prázdných znaků  
 Existuje několik postupů pro zachování prázdných znaků ve zdroji [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pro konečné prezentace, které nejsou ovlivněny [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalizace procesoru prázdné znaky.  
  
 **XML: space = "zachování"**: zadejte tento atribut na úrovni elementu, kde je žádoucí zachování prázdných znaků. Tato uchovává všechny prázdné znaky, které obsahuje mezery, které mohou být přidány úpravy kódu aplikace "pretty print" Zarovnat elementy jako vizuální intuitivní vnoření. Však, zda tyto prostory vykreslení se určuje podle obsahu modelu pro nadřazeného elementu. Neurčujte `xml:space="preserve"` na kořenové úrovni protože většina objektové modely nebere v úvahu bílý prostor významné bez ohledu na to, jak nastavit atribut. Nastavení `xml:space` globálně mohou mít následky výkonu na zpracování (zejména serializace) v některých implementacích XAML. Je doporučeno nastavit pouze atribut konkrétně na úrovni prvků, které se vykreslují mezer v rámci řetězce nebo jsou prázdné místo důležité kolekce.  
  
 **Entity a jiných pevné mezery**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] podporuje všechny uvedení [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] entity v rámci modelu objektu text. Můžete použít vyhrazený entity jako jsou pevné mezery (&\#160; v kódování UTF-8). Můžete také použít ovládací prvky s formátovaným textem, které podporují znaky pevné. Měli byste být opatrní Pokud používáte entity pro simulaci vlastnosti rozložení, jako je například odsazení, protože za běhu výstup entity, které budou záviset na větší počet faktory než by funkce pro výsledky odsazení v typické systém rozložení, jako je například správné použití operátoru panelů a okraje. Pro instanci entity se mapují na písma a můžete změnit velikost v reakci na výběr písma uživatele.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Východoasijské znaky  
 "Východoasijské znaky" je definován jako sada [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] 20000 U + do U + 2FFFD a U + 30000 U + 3FFFD rozsahy adres znak. Tato podmnožina je někdy označovány jako "Ideografické". Další informace najdete na webu [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Modely obsahu prázdné znaky a text  
 V praxi zachování prázdných znaků je pouze z hlediska podmnožina všech možných modely obsahu. Tuto podmnožinu se skládá z obsahu modely, které mohou provádět jednotlivý prvek <xref:System.String> typ v nějaké podobě vyhrazené <xref:System.String> kolekce nebo kombinaci <xref:System.String> a další typy v <xref:System.Collections.IList> nebo <xref:System.Collections.Generic.ICollection%601> kolekce.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Modely obsahu prázdné znaky a text v subsystému WPF  
 Pro ilustraci zbytek tohoto oddílu odkazuje na konkrétní typy, které jsou definovány ve WPF. Zpracování prázdných funkce, které jsou popsány v tomto tématu jsou obecně vztahujících se k rozhraní .NET Framework XAML Services a WPF. Toto chování v akci najdete může vyzkoušet několik značek WPF XAML, zobrazte výsledky v grafu objektů a potom serializovat zpět do kódu znovu.  
  
 Dokonce i pro obsah, který modeluje může trvat řetězce, je výchozí chování v rámci těchto modelů obsahu, že všechny prázdné znaky, které zůstává nepovažoval za významné. Například <xref:System.Windows.Controls.ListBox> přebírá <xref:System.Collections.IList>, ale prázdné znaky (například přečtené mezi jednotlivými <xref:System.Windows.Controls.ListBoxItem>) je Nezachované a není vykresleno. Pokud se pokusíte použít přečtené jako oddělovače mezi řetězce pro <xref:System.Windows.Controls.ListBoxItem> položky, nebude vůbec fungovat; řetězce, které jsou oddělené přečtené jsou považovány za jeden řetězec a jednu položku.  
  
 Těchto kolekcí, které považovat za prázdné místo důležité jsou obvykle součástí modelu dokumentu toku. Primární kolekce, která podporuje zachování prázdných chování je <xref:System.Windows.Documents.InlineCollection>. Tato kolekce třída je deklarována s <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; Pokud tento atribut je nalezen, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesor bude považovat za mezer v rámci kolekce významné. Kombinace `xml:space="preserve"` a mezer v rámci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> označený kolekce je, že se zachovají a vykreslí všechny prázdné znaky. Kombinace `xml:space="default"` a mezer v rámci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> způsobí, že počáteční normalizace prázdné místo je popsáno výše, a které opustí prostorů na některých místech a tyto mezery jsou zachovány a vykreslí. Jaké chování je žádoucí, je na vás a měli byste použít `xml:space` selektivně Chcete-li povolit chování, které chcete.  
  
 Navíc některé vložené prvky, které connote linebreak v modelu dokument toku by měl záměrně kritickému mezeru i v kolekci významné prázdné znaky. Například <xref:System.Windows.Documents.LineBreak> element má ke stejnému účelu jako \<BR / > značku [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]a pro lepší čitelnost v kódu, obvykle <xref:System.Windows.Documents.LineBreak> je oddělen od všechny následující text vytvořené znak odřádkování. Tento znak odřádkování by neměl být normalizovány na stát přední místa na následujícím řádku. Povolit chování, definice třídy pro <xref:System.Windows.Documents.LineBreak> element se vztahuje <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, který je pak interpretována [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesoru k označení tohoto mezery kolem <xref:System.Windows.Documents.LineBreak> vždy oříznut.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Znakové entity XML a XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XML: space v XAML](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
