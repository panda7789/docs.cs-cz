---
title: "XamlName – gramatika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a2d72ea9558003412cc3773e26fb5be751fa19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
