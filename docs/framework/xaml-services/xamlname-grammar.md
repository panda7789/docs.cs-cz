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
ms.openlocfilehash: a39d25f03583ab9020878b7a659bc99489231ff9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458883"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="da9c8-102">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="da9c8-102">XamlName Grammar</span></span>
<span data-ttu-id="da9c8-103">Gramatika v jazyce XAML je specifická gramatika, která je definována ve specifikaci jazyka XAML [MS-XAML], která je zde reprodukována pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="da9c8-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="da9c8-104">Ze specifikace jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="da9c8-104">From the XAML Specification</span></span>  
 <span data-ttu-id="da9c8-105">Specifikace [MS-XAML] definuje gramatiku v jazyce XAML k identifikaci sady platných symbolových identifikátorů použitých pro typy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="da9c8-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="da9c8-106">Řetězcové hodnoty typu XAML musí splňovat následující gramatiky:</span><span class="sxs-lookup"><span data-stu-id="da9c8-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="da9c8-107">Který předpokládá následující obecné hodnoty kategorií, jak je definováno v databázi znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="da9c8-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="da9c8-108">Kategorie sady Unicode</span><span class="sxs-lookup"><span data-stu-id="da9c8-108">Unicode category</span></span>   | <span data-ttu-id="da9c8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="da9c8-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="da9c8-110">Lu</span><span class="sxs-lookup"><span data-stu-id="da9c8-110">Lu</span></span>                 | <span data-ttu-id="da9c8-111">písmeno, velké písmeno</span><span class="sxs-lookup"><span data-stu-id="da9c8-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="da9c8-112">Ll</span><span class="sxs-lookup"><span data-stu-id="da9c8-112">Ll</span></span>                 | <span data-ttu-id="da9c8-113">písmeno, malé písmeno</span><span class="sxs-lookup"><span data-stu-id="da9c8-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="da9c8-114">Lt</span><span class="sxs-lookup"><span data-stu-id="da9c8-114">Lt</span></span>                 | <span data-ttu-id="da9c8-115">písmeno, velké počáteční písmeno</span><span class="sxs-lookup"><span data-stu-id="da9c8-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="da9c8-116">Lm</span><span class="sxs-lookup"><span data-stu-id="da9c8-116">Lm</span></span>                 | <span data-ttu-id="da9c8-117">písmeno, modifikátor</span><span class="sxs-lookup"><span data-stu-id="da9c8-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="da9c8-118">Lo</span><span class="sxs-lookup"><span data-stu-id="da9c8-118">Lo</span></span>                 | <span data-ttu-id="da9c8-119">písmeno, jiné</span><span class="sxs-lookup"><span data-stu-id="da9c8-119">Letter, Other</span></span>                 |
| <span data-ttu-id="da9c8-120">Mn</span><span class="sxs-lookup"><span data-stu-id="da9c8-120">Mn</span></span>                 | <span data-ttu-id="da9c8-121">Značka, bez mezer</span><span class="sxs-lookup"><span data-stu-id="da9c8-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="da9c8-122">MC</span><span class="sxs-lookup"><span data-stu-id="da9c8-122">Mc</span></span>                 | <span data-ttu-id="da9c8-123">značka, kombinování mezer</span><span class="sxs-lookup"><span data-stu-id="da9c8-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="da9c8-124">Nd</span><span class="sxs-lookup"><span data-stu-id="da9c8-124">Nd</span></span>                 | <span data-ttu-id="da9c8-125">Číslo, desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="da9c8-125">Number, Decimal</span></span>               |
| <span data-ttu-id="da9c8-126">NL</span><span class="sxs-lookup"><span data-stu-id="da9c8-126">Nl</span></span>                 | <span data-ttu-id="da9c8-127">číslo, písmeno</span><span class="sxs-lookup"><span data-stu-id="da9c8-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="da9c8-128">XAML definuje druhou gramatiku, DottedXamlName, která se používá pro kvalifikované odkazy na vlastnost a událost a také pro připojené členy.</span><span class="sxs-lookup"><span data-stu-id="da9c8-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="da9c8-129">Další informace naleznete v tématu <xref:System.Windows.DependencyProperty> a [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="da9c8-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="da9c8-130">Hodnoty řetězce, které jsou typu DottedXamlName, musí splňovat následující gramatiky:</span><span class="sxs-lookup"><span data-stu-id="da9c8-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="da9c8-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da9c8-131">Remarks</span></span>  
 <span data-ttu-id="da9c8-132">Kompletní specifikaci naleznete v tématu [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="da9c8-132">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
