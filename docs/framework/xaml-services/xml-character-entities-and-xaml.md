---
title: Znakové entity XML a jazyk XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: b4621da21200e6c9e2b174a0e2ba508a4f6bab92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228195"
---
# <a name="xml-character-entities-and-xaml"></a>Znakové entity XML a jazyk XAML
XAML používá entity znaků, které jsou definované v kódu XML pro zvláštní znaky. Toto téma popisuje některé specifické znakové entity a obecné informace pro další koncepty XML v XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Znakové entity a problémy s uvozovací znaky, které jsou jedinečné pro XAML  
 Značky XAML se obvykle používá stejné znakové entity a řídicí sekvence, které jsou definovány ve formátu XML.  
  
 Hlavní výjimkou je, že složené závorky ({a}) mají význam v XAML, protože tyto znaky informovat XAML procesoru, sekvence znaků uzavřeny ve složených závorkách musí být interpretován jako rozšíření značek. Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek XAML přehled](markup-extensions-for-xaml-overview.md).  
  
 Ale můžete pořád zobrazit složené závorky jako literální znaky pomocí řídicí sekvence, které je specifický pro XAML místo XML. Další informace najdete v tématu [{} řídicí sekvence - rozšíření značek](escape-sequence-markup-extension.md).  
  
 Všimněte si, že zpětné lomítko (\\) nevyžaduje sekvence escape, když je zpracován jako řetězec.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Znakové entity XML  
 Jak už bylo zmíněno dříve, většina znakové entity a řídicí sekvence, které se obvykle používá k zápisu kódu XAML jsou definovány v kódu XML. Toto téma neposkytuje úplný seznam těchto entit; podrobné referenční pro entity, které najdete v externí dokumentace, jako například v specifikace XML. Ale pro usnadnění práce v tomto tématu jsou uvedeny některé specifické znakové entity XML, které se obvykle používají ve značkách XAML.  
  
|Znak|Entity|Poznámky|  
|---------------|------------|-----------|  
|& (znak)|\&amp;|Musíte použít u hodnot atributů a obsahu elementu.|  
|> (větší-než znak)|\&gt;|Musí být použito pro hodnotu atributu, ale > je přijatelné za obsah elementu co nejdelší < nepředchází ho.|  
|< (méně – než znak)|\&lt;|Musí být použito pro hodnotu atributu, ale \< je přijatelné za obsah elementu co nejdelší > ho neřídí.|  
|"(dvojité uvozovky)|\&quot;|Musí být použito pro hodnotu atributu, ale dvojité uvozovky (") je přijatelná obsahu elementu. Všimněte si, že mohou být uzavřeny hodnoty atributů jednoduché uvozovky (') nebo dvojité uvozovky ("); libovolný znak jako první se objeví definuje skříň hodnotu atributu a alternativní nabídky je pak možné jako literál v rámci hodnoty.|  
|"(jednoduché uvozovky)|\&Očekávaný|Musí být použito pro hodnotu atributu, ale jednoduché uvozovky (') je přijatelná obsahu elementu. Všimněte si, že mohou být uzavřeny hodnoty atributů jednoduché uvozovky (') nebo dvojité uvozovky ("); libovolný znak jako první se objeví definuje skříň hodnotu atributu a alternativní nabídky je pak možné jako literál v rámci hodnoty.|  
|(mapování číselný znak)|&#*[číslo]* ; nebo & #x2713 *[hex]*;|XAML podporuje mapování číselný znak do kódování, které je aktivní.|  
|(pevná mezera)|&\#160; (za předpokladu, že kódování UTF-8)|Pro tok elementů dokumentu, ani prvků, které trvat text, například WPF <xref:System.Windows.Controls.TextBox>, nejsou pevných mezer normalizovat mimo kód, dokonce i pro `xml:space="default"`. (Další informace najdete v tématu [– zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formát komentáře XML  
 XAML ve formátu XML komentář: komentář je `<!--`, konec komentáře `-->,` a pořadí `--` nesmí dojít v komentářích.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Pokyny pro zpracování XML  
 XAML zpracovává pokyny pro zpracování XML podle specifikace XML, které stavu pokynů musí předává. XAML zpracování v rozhraní .NET Framework XAML Services nepoužívá žádné instrukce ke zpracování. Další stávajících architektur, které používají XAML nevyužívají pokyny pro zpracování z XAML.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName – gramatika](xamlname-grammar.md)
- [Zpracování prázdných znaků v jazyku XAML](whitespace-processing-in-xaml.md)
