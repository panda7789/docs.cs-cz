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
ms.openlocfilehash: 642ca16142bdfe78a40ddf4e6a3a79ce6a8a4985
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938746"
---
# <a name="xamlname-grammar"></a>XamlName – gramatika
Xamlname – gramatika je konkrétní gramatiky, který je definován ve specifikaci jazyka XAML [MS-XAML], což je reprodukován zde ke zvýšení pohodlí.  
  
## <a name="from-the-xaml-specification"></a>Z specifikaci XAML  
 Specifikace [MS-XAML] definuje gramatiky XamlName ke zjišťování sady právní symbolické identifikátory použitými pro typy a vlastnosti.  
  
 Hodnoty, které jsou typu, který musí odpovídat xamlname – gramatika následující řetězce:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Kde se předpokládá následující hodnoty obecné kategorie definované v databáze znaků Unicode  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML definuje druhý gramatika dottedxamlname –, který se používá pro vlastnost a události kvalifikované odkazy a také pro připojené členy. Další informace najdete v tématu <xref:System.Windows.DependencyProperty> a [přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md).  
  
 Hodnoty, které jsou typu, který musí odpovídat dottedxamlname – gramatika následující řetězce:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompletní specifikaci, naleznete v tématu [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
