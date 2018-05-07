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
ms.openlocfilehash: 5ef489498cdc8716f7599124138f9ecf8945ac9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xml-character-entities-and-xaml"></a>Znakové entity XML a jazyk XAML
XAML používá entity znaků, které jsou definované v kódu XML pro speciální znaky. Toto téma popisuje některé konkrétní znak entit a obecné požadavky na dalších konceptech XML v jazyce XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Znakové entity a problémy uvozovací znaky, které jsou jedinečné pro XAML  
 Kód jazyka XAML se většinou používá stejné entity znaků a řídicích sekvencí, které jsou definovány v kódu XML.  
  
 Hlavní výjimkou je, který složené závorky ({a}) mají význam v jazyce XAML, protože tyto znaky informovat procesor XAML posloupnost znaků uvedené ve složených závorkách musí být interpretaci jako rozšíření značek. Další informace o rozšíření značek najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 Ale můžete pořád zobrazit složené závorky jako literály pomocí řídicí sekvence, které je specifický pro XAML místo XML. Další informace najdete v tématu [ {} řídicí sekvence – rozšíření značek](escape-sequence-markup-extension.md).  
  
 Všimněte si, že zpětné lomítko (\\) nevyžaduje řídicí sekvence, pokud se zpracovává jako řetězec.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Znakové entity XML  
 Jak je uvedeno nahoře, většina entity znaků a řídicích sekvencí, které jsou obvykle používány k zápisu kódu XAML jsou definovány XML. Toto téma neposkytuje úplný seznam těchto entitách; podrobné referenční pro entity naleznete v dokumentaci k externí, jako v specifikace XML. Ale pro usnadnění práce v tomto tématu jsou uvedeny některé konkrétní znakové entity XML, které jsou obvykle používány v XAML značek.  
  
|Znak|Entity|Poznámky|  
|---------------|------------|-----------|  
|& (ampersand)|\&amp;|Musí použít u hodnot atributů i obsahu elementu.|  
|> (větší – než znak)|\&gt;|Je nutné použít hodnotu atributu, ale > je přijatelné jako obsah stejně dlouho jako element < není předcházet.|  
|< (menší – než znak)|\&lt;|Je nutné použít hodnotu atributu, ale \< je přijatelné jako obsah elementu stejně dlouho jako > nedodrží ho.|  
|"(dvojité uvozovky)|\&Automatické formátování výše.|Je nutné použít hodnotu atributu, ale dvojité uvozovky (") se dá použít jako obsahu elementu. Všimněte si, že hodnoty atributu může být uzavřená pomocí přímých apostrof (') nebo pomocí dvojité uvozovky ("); podle toho, která znak zobrazí první definuje skříni hodnotu atributu a alternativní uvozovky lze jako literál v hodnotě.|  
|' (jednoduché uvozovky)|\&APOS;|Je nutné použít hodnotu atributu, ale je přijatelné jako obsah elementu přímých apostrof ('). Všimněte si, že hodnoty atributu může být uzavřená pomocí přímých apostrof (') nebo pomocí dvojité uvozovky ("); podle toho, která znak zobrazí první definuje skříni hodnotu atributu a alternativní uvozovky lze jako literál v hodnotě.|  
|(čísla mapování)|&#*[celé číslo]* ; nebo & #x *[šestnáctkových]*;|XAML podporuje mapování čísla do kódování, které je aktivní.|  
|(pevná místa)|&\#160; (za předpokladu, že kódování UTF-8)|Pro prvky toku dokumentu nebo prvky, které trvat text například WPF <xref:System.Windows.Controls.TextBox>, pevné mezery nejsou normalized mimo značku, i pro `xml:space="default"`. (Další informace najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formát komentáře XML  
 XAML používá formát komentáře XML: spuštění komentář je `<!--`, je na konci komentáře `-->,` a pořadí `--` nesmí vyskytovat v rámci komentář.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Pokyny pro zpracování XML  
 XAML zpracovává pokyny pro zpracování XML podle specifikace XML, které stavu pokynů musí předána. XAML zpracování v rozhraní .NET Framework XAML Services nepoužívá instrukcí pro zpracování. Jiné existující rozhraní používající XAML také nepoužívejte pokyny pro zpracování z XAML.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XamlName – gramatika](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [Zpracování prázdných znaků v jazyku XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
