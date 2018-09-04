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
ms.openlocfilehash: 2a934316517047da6b6aec8e88026024b9a25f65
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514798"
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
  
 XAML definuje druhý gramatika dottedxamlname –, který se používá pro vlastnost a události kvalifikované odkazy a také pro připojené členy. Další informace najdete v tématu <xref:System.Windows.DependencyProperty> a [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Hodnoty, které jsou typu, který musí odpovídat dottedxamlname – gramatika následující řetězce:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompletní specifikaci, naleznete v tématu [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
