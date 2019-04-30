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
# <a name="xamlname-grammar"></a><span data-ttu-id="ae5e5-102">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="ae5e5-102">XamlName Grammar</span></span>
<span data-ttu-id="ae5e5-103">Xamlname – gramatika je konkrétní gramatiky, který je definován ve specifikaci jazyka XAML [MS-XAML], což je reprodukován zde ke zvýšení pohodlí.</span><span class="sxs-lookup"><span data-stu-id="ae5e5-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="ae5e5-104">Z specifikaci XAML</span><span class="sxs-lookup"><span data-stu-id="ae5e5-104">From the XAML Specification</span></span>  
 <span data-ttu-id="ae5e5-105">Specifikace [MS-XAML] definuje gramatiky XamlName ke zjišťování sady právní symbolické identifikátory použitými pro typy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ae5e5-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="ae5e5-106">Hodnoty, které jsou typu, který musí odpovídat xamlname – gramatika následující řetězce:</span><span class="sxs-lookup"><span data-stu-id="ae5e5-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="ae5e5-107">Kde se předpokládá následující hodnoty obecné kategorie definované v databáze znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="ae5e5-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  
  
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
  
 <span data-ttu-id="ae5e5-108">XAML definuje druhý gramatika dottedxamlname –, který se používá pro vlastnost a události kvalifikované odkazy a také pro připojené členy.</span><span class="sxs-lookup"><span data-stu-id="ae5e5-108">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="ae5e5-109">Další informace najdete v tématu <xref:System.Windows.DependencyProperty> a [přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ae5e5-109">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
 <span data-ttu-id="ae5e5-110">Hodnoty, které jsou typu, který musí odpovídat dottedxamlname – gramatika následující řetězce:</span><span class="sxs-lookup"><span data-stu-id="ae5e5-110">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae5e5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae5e5-111">Remarks</span></span>  
 <span data-ttu-id="ae5e5-112">Kompletní specifikaci, naleznete v tématu [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="ae5e5-112">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
