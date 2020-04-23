---
title: XamlName – gramatika
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071827"
---
# <a name="xamlname-grammar"></a>XamlName – gramatika

XamlName Grammar je specifická gramatika, která je definována ve specifikaci jazyka XAML [MS-XAML], která je zde reprodukována pro pohodlí.

## <a name="from-the-xaml-specification"></a>Ze specifikace XAML

Specifikace [MS-XAML] definuje gramatiku XamlName k identifikaci sady právních symbolických identifikátorů používaných pro typy a vlastnosti.

Řetězcové hodnoty typu XamlName musí odpovídat následující gramatice:

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

Který předpokládá následující obecné hodnoty kategorií, jak jsou definovány v databázi znaků Unicode

| Kategorie Unicode   | Popis                   |
|--------------------|-------------------------------|
| Lu                 | písmeno, velké písmeno             |
| Ll                 | písmeno, malé písmeno             |
| Lt                 | písmeno, velké počáteční písmeno             |
| Lm                 | písmeno, modifikátor              |
| Lo                 | písmeno, jiné                 |
| Mn                 | Označit, nemezery             |
| Mc                 | značka, kombinování mezer       |
| Nd                 | Číslo, desetinné číslo               |
| Nl                 | číslo, písmeno                |

XAML definuje druhou gramatiku DottedXamlName, která se používá pro odkazy na vlastnosti a události a také pro připojené členy. Další informace naleznete <xref:System.Windows.DependencyProperty> v tématu a [Přehled XAML (WPF)](../fundamentals/xaml.md).

Řetězcové hodnoty typu DottedXamlName musí odpovídat následující gramatice:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Poznámky

Kompletní specifikaci naleznete v tématu [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
