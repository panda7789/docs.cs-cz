---
title: "Zpracování prázdných znaků v jazyku XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], whitespace processing
- whitespace processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 80b75897f54136849aa4b356c414145510d9cd3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="whitespace-processing-in-xaml"></a>Zpracování prázdných znaků v jazyku XAML
Jazyk pravidel pro jazyk XAML stavu, je nutné zpracovat tuto významný mezerový znak [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementace procesoru. Toto téma popisuje tato pravidla jazyka XAML. Je také dokumenty zpracování další prázdný znak, který je definován [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementace procesoru XAML a zapisovače XAML pro serializaci.  
  
<a name="whitespace_definition"></a>   
## <a name="whitespace-definition"></a>Definice prázdné znaky  
 Konzistentní s [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], prázdné znaky v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jsou místa, konce řádku a karty. Tyto odpovídají [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] hodnoty 0020, 000A a 0009 v uvedeném pořadí.  
  
<a name="whitespace_normalization"></a>   
## <a name="whitespace-normalization"></a>Normalizaci prázdné znaky  
 Ve výchozím nastavení dojde k následující normalizaci prázdných znaků při [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesů procesoru [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] souboru:  
  
1.  Znaky konce řádku východoasijských znaků, se odeberou. Najdete v části "Východoasijské znaky" dál v tomto tématu pro definici tohoto termínu.  
  
2.  Všechny prázdné znaky (místa, konce řádku, karta) se převedou na prostory.  
  
3.  Všechny prostory po sobě jdoucích jsou odstraněna a nahrazena jediného místa.  
  
4.  Místa, hned za počáteční značky je odstraněn.  
  
5.  Místo bezprostředně před koncová značka je odstraněn.  
  
 "Výchozí" odpovídá stavu označený jako výchozí hodnota [XML: Space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) atribut.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="whitespace-in-inner-text-and-string-primitives"></a>Prázdné znaky na vnitřní Text a řetězce primitiv  
 Předchozí pravidla normalizace platí pro vnitřní text, který se nachází v rámci elementů XAML. Po normalizaci procesor XAML převede všechny vnitřní text do příslušného typu následujícím způsobem:  
  
-   Pokud typ vlastnosti není kolekce, ale není přímo <xref:System.Object> typ procesoru XAML pokusí převést na tento typ pomocí jeho převaděče typů. Selhání převodu zde způsobí, že chyby kompilace.  
  
-   Pokud je typ vlastnosti kolekce a je souvislý vnitřní text (žádné použité element značky), je jako jeden analyzovat vnitřní text <xref:System.String>. Pokud typ kolekce nemůže přijmout <xref:System.String>, to také způsobí, že chyby kompilace.  
  
-   Pokud je typ vlastnosti <xref:System.Object>, je jako jeden analyzovat vnitřní text <xref:System.String>. Existuje jsou uplynulého značky elementu, způsobí, že k chybě kompilace protože <xref:System.Object> typ znamená jednoho objektu (<xref:System.String> nebo jinak).  
  
-   Pokud je typ proměnné kolekce, a vnitřní text není souvislý, je první dílčí řetězec převést na <xref:System.String> a přidali jako položku kolekce, použité prvek přidán jako položku kolekce, a nakonec je koncové dílčí řetězec (pokud existuje) Přidat do kolekce jako třetí <xref:System.String> položky.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-whitespace"></a>Zachování prázdné znaky  
 Existuje několik postupů pro zachování prázdné znaky na zdroji [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pro případné prezentace, které neovlivňuje [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalizaci procesoru prázdný znak.  
  
 **XML: space = "zachovat"**: zadejte tento atribut na úrovni elementu, kde je žádoucí písmen a zachovávání prázdný znak. Tato uchovává všechny prázdné znaky, které obsahuje mezery, které mohou být přidány úpravu kódu aplikace "pretty tisk" Zarovnat elementy jako vizuálně intuitivní vnoření. Ale jestli těchto prostorů vykreslení je určen podle modelu obsahu nadřazeného elementu. Vyhněte se zadání `xml:space="preserve"` na kořenové úrovni protože většina objektové modely Neberte v úvahu prázdné znaky jako významné bez ohledu na to jak nastavit atribut. Nastavení `xml:space` globálně může mít důsledky výkonu na zpracování (zejména serializace) v některých implementacích XAML. Je vhodnější pouze nastavit atribut konkrétně na úrovni elementů, které vykreslení prázdné znaky uvnitř řetězců, nebo jsou významné kolekce prázdný znak.  
  
 **Entity a pevné mezery**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] podporuje všechny umístění [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] entity v rámci modelu objektu text. Vyhrazené entity můžete použít například pevné mezery (&\#160; v kódování UTF-8). Můžete také použít ovládací prvky RTF, které podporují pevných mezer. Buďte opatrní Pokud používáte entity k simulaci rozložení charakteristiky jako odsazení, protože výstup spuštění entity se liší podle větší několika faktory, než by možnosti pro vytvoření výsledky odsazení v typické rozložení systému, například správné použití operátoru panelů a okraje. Pro instanci entity jsou namapované na písma a můžete změnit velikost v reakci na výběr písma uživatele.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Východoasijské znaky  
 "Východoasijské znaky" je definován jako sadu [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] znak rozsahy U + 20000 U + 2FFFD a U + 30000 U + 3FFFD. Tato část se také někdy označuje jako "Znaky CJK". Další informace najdete v tématu [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="whitespace-and-text-content-models"></a>Prázdné znaky a textového obsahu modely  
 V praxi zachování prázdný znak je pouze z hlediska podmnožinu všechny možné obsahu modely. Tuto podmnožinu se skládá z obsahu modely, které může provádět typu singleton <xref:System.String> typu v některé formuláře vyhrazená <xref:System.String> kolekce nebo s kombinaci těchto možností <xref:System.String> a dalších typů v <xref:System.Collections.IList> nebo <xref:System.Collections.Generic.ICollection%601> kolekce.  
  
### <a name="whitespace-and-text-content-models-in-wpf"></a>Prázdné znaky a textového obsahu modely v grafickém subsystému WPF  
 Pro účely obrázek zbytek této části odkazuje na konkrétní typy, které jsou definovány WPF. Zpracování prázdných znaků funkce, které jsou popsané v tomto tématu jsou obecně vztahujících se k rozhraní .NET Framework XAML Services a WPF. Toto chování v akci najdete můžete experimentovat s některé kódu WPF XAML, zobrazte výsledky v grafu objektů a pak serializovat zpět na kód znovu.  
  
 I pro modely obsah, který může trvat řetězce, použije se výchozí chování v rámci těchto modelů obsahu je, že všechny prázdné znaky, které zůstává není zpracováván jako důležité. Například <xref:System.Windows.Controls.ListBox> trvá <xref:System.Collections.IList>, ale prázdné znaky (například přečtené mezi jednotlivými <xref:System.Windows.Controls.ListBoxItem>) není zachována a není vykreslen. Pokud se pokusíte použít přečtené jako oddělovače mezi řetězce pro <xref:System.Windows.Controls.ListBoxItem> položek, nefunguje vůbec; řetězce, které jsou odděleny přečtené jsou považovány za jeden řetězec a jednu položku.  
  
 Tyto kolekce, které považovat za prázdné významné jsou obvykle součástí model toku dokumentu. Primární kolekce, která podporuje prázdné zachovávání chování je <xref:System.Windows.Documents.InlineCollection>. Tato třída kolekce je deklarovaný s <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; Pokud je tento atribut nalezen, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesoru bude považovat za prázdných znaků v rámci kolekce významné. Kombinace `xml:space="preserve"` a prázdných znaků v rámci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> označený jako kolekce je, že je zachována a vykresluje všechny prázdné znaky. Kombinace `xml:space="default"` a prázdných znaků v rámci <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> příčin normalizaci počáteční prázdné popsané výše, a tím opustí jediného místa v určitých pozic a těchto prostorů jsou uchování a vykreslen. Jaké chování je žádoucí, je na vás a měli byste použít `xml:space` selektivně k chování, které chcete povolit.  
  
 Některé vložené prvky, které connote linebreak v modelu dokument toku také vhodné zavést záměrně není mezeru i v kolekci významné prázdné znaky. Například <xref:System.Windows.Documents.LineBreak> element má ke stejnému účelu jako \<BR / > značky v [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]a čitelnější v značek, obvykle <xref:System.Windows.Documents.LineBreak> z jakékoli následné textu oddělených vytvořené konce řádku. Tento konce řádku nesmí budou normalizovány na stát úvodní mezery v následujícím řádku. Povolit daná chování definici třídy <xref:System.Windows.Documents.LineBreak> element se vztahuje <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, který je pak interpretována [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesor znamená, že kolem prázdný znak <xref:System.Windows.Documents.LineBreak> je vždy oříznut.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Znakové entity XML a jazyk XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [XML: space v jazyce XAML](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
