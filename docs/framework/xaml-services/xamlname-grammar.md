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
ms.openlocfilehash: 92327c8ff6232e64bf8b6b2a9d78e4a9eb30f3e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xamlname-grammar"></a><span data-ttu-id="e87ef-102">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="e87ef-102">XamlName Grammar</span></span>
<span data-ttu-id="e87ef-103">XamlName – gramatika je konkrétní gramatika, která je definována v specifikace jazyka XAML [MS XAML], který je zde uveden ke zvýšení pohodlí.</span><span class="sxs-lookup"><span data-stu-id="e87ef-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="e87ef-104">Z specifikace jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="e87ef-104">From the XAML Specification</span></span>  
 <span data-ttu-id="e87ef-105">Specifikace [MS-XAML] definuje gramatika XamlName k určení sady právní symbolický identifikátory používané pro různé typy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e87ef-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="e87ef-106">Řetězce hodnoty, které jsou typu, který XamlName musí odpovídat následující gramatikou:</span><span class="sxs-lookup"><span data-stu-id="e87ef-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="e87ef-107">Kde se předpokládá následující obecné kategorie hodnoty definovaným v databázi znak Unicode</span><span class="sxs-lookup"><span data-stu-id="e87ef-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  
  
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
  
 <span data-ttu-id="e87ef-108">XAML definuje druhý – gramatika dottedxamlname –, který se používá pro vlastnosti a události kvalifikovaný odkazy a také pro připojené členy.</span><span class="sxs-lookup"><span data-stu-id="e87ef-108">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="e87ef-109">Další informace najdete v tématu <xref:System.Windows.DependencyProperty> a [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="e87ef-109">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
 <span data-ttu-id="e87ef-110">Řetězce hodnoty, které jsou typu, který musí odpovídat dottedxamlname – gramatika následující:</span><span class="sxs-lookup"><span data-stu-id="e87ef-110">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="e87ef-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e87ef-111">Remarks</span></span>  
 <span data-ttu-id="e87ef-112">Specifikace dokončení najdete v části [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="e87ef-112">For the complete specification, see [\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
