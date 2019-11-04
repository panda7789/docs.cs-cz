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
ms.openlocfilehash: 92bf49ac1ae67fb8d2e268eeaaf63cd72d9f6251
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458814"
---
# <a name="xml-character-entities-and-xaml"></a>Znakové entity XML a jazyk XAML
XAML používá znakové entity definované v XML pro speciální znaky. Toto téma popisuje některé konkrétní znakové entity a obecné pokyny pro další koncepty XML v jazyce XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Znakové entity a uvozovací problémy, které jsou jedinečné pro XAML  
 Kód XAML obvykle používá stejné znakové entity a řídicí sekvence, které jsou definovány v XML.  
  
 Hlavní výjimkou je, že složené závorky ({a}) mají význam v jazyce XAML, protože tyto znaky informují procesor XAML o tom, že znaková sekvence uzavřená složenými závorkami musí být interpretována jako rozšíření značek. Další informace o rozšíření značek naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
 Můžete však stále zobrazit složené závorky jako literální znaky pomocí řídicí sekvence, která je určena pouze pro XAML namísto XML. Další informace najdete v tématu [{} sekvence escape – rozšíření značek](escape-sequence-markup-extension.md).  
  
 Všimněte si, že zpětné lomítko (\\) nevyžaduje řídicí sekvenci, pokud je zpracována jako řetězec.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Znakové entity XML  
 Jak již bylo zmíněno dříve, většina znakových entit a řídicích sekvencí, které jsou obvykle použity pro zápis kódu XAML, jsou definovány kódem XML. Toto téma neuvádí úplný seznam těchto entit. Podrobné informace o entitách najdete v externí dokumentaci, jako jsou specifikace XML. Pro usnadnění ale toto téma uvádí některé z konkrétních entit znakové sady XML, které se obvykle používají v kódu XAML.  
  
|Znak|Entity|Poznámky|  
|---------------|------------|-----------|  
|& (ampersand)|\&amp;|Musí být použit pro hodnoty atributů i pro obsah elementu.|  
|> (větší než znak)|\&gt;|Musí být použit pro hodnotu atributu, ale > je přijatelné jako obsah elementu, dokud < nepředchází před ním.|  
|< (menší než znak)|\&lt;|Musí být použit pro hodnotu atributu, ale \< je přijatelné jako obsah elementu, dokud > nedodržuje.|  
|"(přímá uvozovka)|\&quot;|Musí být použit pro hodnotu atributu, ale rovné uvozovky (") jsou přijatelné jako obsah elementu. Všimněte si, že hodnoty atributu můžou být uzavřeny buď jednou rovnou uvozovkou ('), nebo přímou uvozovkou ("); podle toho, který znak se zobrazí, je nejprve definována hodnota atributu a v rámci hodnoty lze použít alternativní uvozovky jako literál.|  
|' (jednoduchá uvozovka)|\&{0};|Musí být použit pro hodnotu atributu, ale jedna znaková uvozovka (') je přijatelná jako obsah elementu. Všimněte si, že hodnoty atributu můžou být uzavřeny buď jednou rovnou uvozovkou ('), nebo přímou uvozovkou ("); podle toho, který znak se zobrazí, je nejprve definována hodnota atributu a v rámci hodnoty lze použít alternativní uvozovky jako literál.|  
|(mapování číselných znaků)|&# *[Integer]* ; nebo & #x *[hex]* ;|XAML podporuje mapování číselných znaků do kódování, které je aktivní.|  
|(nerozdělitelné místo)|&\#160; (předpokládá se kódování UTF-8)|Pro prvky dokumentu Flow nebo prvky, které přijímají text jako <xref:System.Windows.Controls.TextBox>WPF, neoddělovací mezery nejsou normalizovány mimo značky, a to ani pro `xml:space="default"`. (Další informace naleznete v tématu [prázdné místo zpracování v jazyce XAML](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Formát komentáře XML  
 XAML používá formát komentáře XML: začátek komentáře je `<!--`, konec komentáře je `-->,` a `--` sekvence se nesmí nacházet v rámci komentáře.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Pokyny pro zpracování XML  
 Jazyk XAML zpracovává instrukce pro zpracování XML podle specifikací XML, což uvádí, že instrukce musí být předány prostřednictvím. Zpracování XAML v .NET Framework služby XAML nepoužívá žádné instrukce pro zpracování. Jiná existující rozhraní, která používají XAML, nepoužívají také instrukce pro zpracování z XAML.  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName – gramatika](xamlname-grammar.md)
- [Zpracování prázdných míst v jazyce XAML](whitespace-processing-in-xaml.md)
