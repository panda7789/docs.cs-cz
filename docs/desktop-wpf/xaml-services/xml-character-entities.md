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
ms.openlocfilehash: aff96c5d0ee6bbf2bbe2f9e3b3ae091caa781f7a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071456"
---
# <a name="xml-character-entities-and-xaml"></a>Znakové entity XML a jazyk XAML

XAML používá znakové entity definované v JAZYCE XML pro speciální znaky. Toto téma popisuje některé specifické entity znaků a obecné aspekty pro jiné koncepty XML v jazyce XAML.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entity znaků a úniky problémy, které jsou jedinečné pro XAML

Značky XAML obvykle používají stejné entity znaků a řídicí sekvence, které jsou definovány v jazyce XML.

Hlavní výjimkou je, že složená závorky ({ a }) mají význam v XAML, protože tyto znaky informují procesor XAML, že sekvence znaků uzavřená závorkami musí být interpretována jako rozšíření značek. Další informace o rozšířeních značek naleznete v [tématu Markup Extensions for XAML Overview](markup-extensions-overview.md).

Však můžete stále zobrazit závorky jako literál znaky pomocí sekvence escape, která je zvláštní XAML místo XML. Další informace naleznete v [ {} tématu Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).

Všimněte si,\\že zpětné lomítko ( ) nevyžaduje řídicí sekvenci, pokud je zpracována jako řetězec.

## <a name="xml-character-entities"></a>Entity znaků XML

Jak již bylo zmíněno dříve, většina znakových entit a řídicích sekvencí, které se obvykle používají k zápisu značek XAML, jsou definovány jazykem XML. Toto téma neposkytuje úplný seznam těchto entit. podrobný odkaz na entity naleznete v externí dokumentaci, například ve specifikacích XML. Pro větší pohodlí však toto téma uvádí některé konkrétní entity znaků XML, které se obvykle používají ve značkách XAML.

|Znak|Entita|Poznámky|
|---------------|------------|-----------|
|& (ampersand)|\&a)|Musí být použit pro hodnoty atributů a pro obsah prvku.|
|> (větší než znak)|\&gt;|Musí být použit pro hodnotu atributu, ale > je přijatelné jako obsah prvku tak dlouho, dokud < nepředchází.|
|< (méně než znak)|\&To;|Musí být použit pro hodnotu atributu, ale \< je přijatelné jako obsah prvku tak dlouho, dokud > nenásleduje.|
|" (kurzní uvozovky)|\&quot;|Musí být použit pro hodnotu atributu, ale přímé uvozovky (") je přijatelné jako obsah prvku. Všimněte si, že hodnoty atributů mohou být uzavřeny buď jedním přímým uvozovkovým uvozovkam ('), nebo rovnou uvozovkou ("); podle toho, který znak se objeví jako první definuje skříň hodnoty atributu a alternativní uvozovky pak lze použít jako literál v rámci hodnoty.|
|' (jednoduché přímé uvozovky)|\&apos;|Musí být použit pro hodnotu atributu, ale jeden rovný uvozovky (') je přijatelné jako obsah prvku. Všimněte si, že hodnoty atributů mohou být uzavřeny buď jedním přímým uvozovkovým uvozovkam ('), nebo rovnou uvozovkou ("); podle toho, který znak se objeví jako první definuje skříň hodnoty atributu a alternativní uvozovky pak lze použít jako literál v rámci hodnoty.|
|(číselná mapování znaků)|&#*[celé číslo]*; nebo & #x *[hex]*;|XAML podporuje mapování číselných znaků do kódování, které je aktivní.|
|(nerozdělitý prostor)|&\#160; (za předpokladu kódování UTF-8)|Pro prvky toku dokumentu nebo prvky, <xref:System.Windows.Controls.TextBox>které přebírají text, jako je například `xml:space="default"`WPF , nerozdělitelné mezery nejsou normalizovány mimo značky, a to ani pro . (Další informace naleznete [v tématu White-space processing in XAML](white-space-processing.md).)|

## <a name="xml-comment-format"></a>Formát komentáře XML

XAML používá formát komentáře XML: začátek `<!--`komentáře je , `-->,` konec `--` komentáře je a sekvence nesmí dojít v komentáři.

## <a name="xml-processing-instructions"></a>Pokyny pro zpracování XML

XAML zpracovává pokyny pro zpracování XML podle specifikací XML, které uvádějí, že pokyny musí být předány. Zpracování XAML ve službě .NET XAML services nepoužívá žádné pokyny pro zpracování. Jiné existující architektury, které používají XAML také nepoužívají pokyny pro zpracování z XAML.

## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName – gramatika](xamlname-grammar.md)
- [Zpracování prázdných znaků v jazyku XAML](white-space-processing.md)
