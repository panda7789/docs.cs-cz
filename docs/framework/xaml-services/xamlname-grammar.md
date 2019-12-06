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
# <a name="xamlname-grammar"></a><span data-ttu-id="48682-102">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="48682-102">XamlName Grammar</span></span>
<span data-ttu-id="48682-103">Gramatika v jazyce XAML je specifická gramatika, která je definována ve specifikaci jazyka XAML [MS-XAML], která je zde reprodukována pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="48682-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="48682-104">Ze specifikace jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="48682-104">From the XAML Specification</span></span>  
 <span data-ttu-id="48682-105">Specifikace [MS-XAML] definuje gramatiku v jazyce XAML k identifikaci sady platných symbolových identifikátorů použitých pro typy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48682-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="48682-106">Řetězcové hodnoty typu XAML musí splňovat následující gramatiky:</span><span class="sxs-lookup"><span data-stu-id="48682-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="48682-107">Který předpokládá následující obecné hodnoty kategorií, jak je definováno v databázi znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="48682-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="48682-108">Kategorie sady Unicode</span><span class="sxs-lookup"><span data-stu-id="48682-108">Unicode category</span></span>   | <span data-ttu-id="48682-109">Popis</span><span class="sxs-lookup"><span data-stu-id="48682-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="48682-110">Lu</span><span class="sxs-lookup"><span data-stu-id="48682-110">Lu</span></span>                 | <span data-ttu-id="48682-111">písmeno, velké písmeno</span><span class="sxs-lookup"><span data-stu-id="48682-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="48682-112">Ll</span><span class="sxs-lookup"><span data-stu-id="48682-112">Ll</span></span>                 | <span data-ttu-id="48682-113">písmeno, malé písmeno</span><span class="sxs-lookup"><span data-stu-id="48682-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="48682-114">Lt</span><span class="sxs-lookup"><span data-stu-id="48682-114">Lt</span></span>                 | <span data-ttu-id="48682-115">písmeno, velké počáteční písmeno</span><span class="sxs-lookup"><span data-stu-id="48682-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="48682-116">Lm</span><span class="sxs-lookup"><span data-stu-id="48682-116">Lm</span></span>                 | <span data-ttu-id="48682-117">písmeno, modifikátor</span><span class="sxs-lookup"><span data-stu-id="48682-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="48682-118">Lo</span><span class="sxs-lookup"><span data-stu-id="48682-118">Lo</span></span>                 | <span data-ttu-id="48682-119">písmeno, jiné</span><span class="sxs-lookup"><span data-stu-id="48682-119">Letter, Other</span></span>                 |
| <span data-ttu-id="48682-120">Mn</span><span class="sxs-lookup"><span data-stu-id="48682-120">Mn</span></span>                 | <span data-ttu-id="48682-121">Značka, bez mezer</span><span class="sxs-lookup"><span data-stu-id="48682-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="48682-122">MC</span><span class="sxs-lookup"><span data-stu-id="48682-122">Mc</span></span>                 | <span data-ttu-id="48682-123">značka, kombinování mezer</span><span class="sxs-lookup"><span data-stu-id="48682-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="48682-124">Nd</span><span class="sxs-lookup"><span data-stu-id="48682-124">Nd</span></span>                 | <span data-ttu-id="48682-125">Číslo, desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="48682-125">Number, Decimal</span></span>               |
| <span data-ttu-id="48682-126">NL</span><span class="sxs-lookup"><span data-stu-id="48682-126">Nl</span></span>                 | <span data-ttu-id="48682-127">číslo, písmeno</span><span class="sxs-lookup"><span data-stu-id="48682-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="48682-128">XAML definuje druhou gramatiku, DottedXamlName, která se používá pro kvalifikované odkazy na vlastnost a událost a také pro připojené členy.</span><span class="sxs-lookup"><span data-stu-id="48682-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="48682-129">Další informace naleznete v tématu <xref:System.Windows.DependencyProperty> a [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="48682-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="48682-130">Hodnoty řetězce, které jsou typu DottedXamlName, musí splňovat následující gramatiky:</span><span class="sxs-lookup"><span data-stu-id="48682-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="48682-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48682-131">Remarks</span></span>  
 <span data-ttu-id="48682-132">Kompletní specifikaci naleznete v tématu [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="48682-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
