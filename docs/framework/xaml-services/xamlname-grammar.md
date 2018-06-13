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
ms.openlocfilehash: 32fd7b7b952ebbc853e41c0a8276d1ab487e619f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561888"
---
# <a name="xamlname-grammar"></a>XamlName – gramatika
XamlName – gramatika je konkrétní gramatika, která je definována v specifikace jazyka XAML [MS XAML], který je zde uveden ke zvýšení pohodlí.  
  
## <a name="from-the-xaml-specification"></a>Z specifikace jazyka XAML  
 Specifikace [MS-XAML] definuje gramatika XamlName k určení sady právní symbolický identifikátory používané pro různé typy a vlastnosti.  
  
 Řetězce hodnoty, které jsou typu, který XamlName musí odpovídat následující gramatikou:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Kde se předpokládá následující obecné kategorie hodnoty definovaným v databázi znak Unicode  
  
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
  
 XAML definuje druhý – gramatika dottedxamlname –, který se používá pro vlastnosti a události kvalifikovaný odkazy a také pro připojené členy. Další informace najdete v tématu <xref:System.Windows.DependencyProperty> a [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Řetězce hodnoty, které jsou typu, který musí odpovídat dottedxamlname – gramatika následující:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Poznámky  
 Specifikace dokončení najdete v části [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).
