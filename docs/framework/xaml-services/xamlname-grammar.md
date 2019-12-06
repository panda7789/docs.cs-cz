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
ms.openlocfilehash: a1e7a5a03db4a24ed4d13d62899754cfe9e76b56
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837152"
---
# <a name="xamlname-grammar"></a>XamlName – gramatika
Gramatika v jazyce XAML je specifická gramatika, která je definována ve specifikaci jazyka XAML [MS-XAML], která je zde reprodukována pro usnadnění.  
  
## <a name="from-the-xaml-specification"></a>Ze specifikace jazyka XAML  
 Specifikace [MS-XAML] definuje gramatiku v jazyce XAML k identifikaci sady platných symbolových identifikátorů použitých pro typy a vlastnosti.  
  
 Řetězcové hodnoty typu XAML musí splňovat následující gramatiky:  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Který předpokládá následující obecné hodnoty kategorií, jak je definováno v databázi znaků Unicode.  

| Kategorie sady Unicode   | Popis                   |
|--------------------|-------------------------------|
| Lu                 | písmeno, velké písmeno             |
| Ll                 | písmeno, malé písmeno             |
| Lt                 | písmeno, velké počáteční písmeno             |
| Lm                 | písmeno, modifikátor              |
| Lo                 | písmeno, jiné                 |
| Mn                 | Značka, bez mezer             |
| MC                 | značka, kombinování mezer       |
| Nd                 | Číslo, desetinné číslo               |
| NL                 | číslo, písmeno                |
 
 XAML definuje druhou gramatiku, DottedXamlName, která se používá pro kvalifikované odkazy na vlastnost a událost a také pro připojené členy. Další informace naleznete v tématu <xref:System.Windows.DependencyProperty> a [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).  
  
 Hodnoty řetězce, které jsou typu DottedXamlName, musí splňovat následující gramatiky:  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompletní specifikaci naleznete v tématu [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
