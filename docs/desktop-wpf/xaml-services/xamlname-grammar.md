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
# <a name="xamlname-grammar"></a><span data-ttu-id="110da-102">XamlName – gramatika</span><span class="sxs-lookup"><span data-stu-id="110da-102">XamlName Grammar</span></span>

<span data-ttu-id="110da-103">XamlName Grammar je specifická gramatika, která je definována ve specifikaci jazyka XAML [MS-XAML], která je zde reprodukována pro pohodlí.</span><span class="sxs-lookup"><span data-stu-id="110da-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="110da-104">Ze specifikace XAML</span><span class="sxs-lookup"><span data-stu-id="110da-104">From the XAML Specification</span></span>

<span data-ttu-id="110da-105">Specifikace [MS-XAML] definuje gramatiku XamlName k identifikaci sady právních symbolických identifikátorů používaných pro typy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="110da-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="110da-106">Řetězcové hodnoty typu XamlName musí odpovídat následující gramatice:</span><span class="sxs-lookup"><span data-stu-id="110da-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="110da-107">Který předpokládá následující obecné hodnoty kategorií, jak jsou definovány v databázi znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="110da-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="110da-108">Kategorie Unicode</span><span class="sxs-lookup"><span data-stu-id="110da-108">Unicode category</span></span>   | <span data-ttu-id="110da-109">Popis</span><span class="sxs-lookup"><span data-stu-id="110da-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="110da-110">Lu</span><span class="sxs-lookup"><span data-stu-id="110da-110">Lu</span></span>                 | <span data-ttu-id="110da-111">písmeno, velké písmeno</span><span class="sxs-lookup"><span data-stu-id="110da-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="110da-112">Ll</span><span class="sxs-lookup"><span data-stu-id="110da-112">Ll</span></span>                 | <span data-ttu-id="110da-113">písmeno, malé písmeno</span><span class="sxs-lookup"><span data-stu-id="110da-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="110da-114">Lt</span><span class="sxs-lookup"><span data-stu-id="110da-114">Lt</span></span>                 | <span data-ttu-id="110da-115">písmeno, velké počáteční písmeno</span><span class="sxs-lookup"><span data-stu-id="110da-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="110da-116">Lm</span><span class="sxs-lookup"><span data-stu-id="110da-116">Lm</span></span>                 | <span data-ttu-id="110da-117">písmeno, modifikátor</span><span class="sxs-lookup"><span data-stu-id="110da-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="110da-118">Lo</span><span class="sxs-lookup"><span data-stu-id="110da-118">Lo</span></span>                 | <span data-ttu-id="110da-119">písmeno, jiné</span><span class="sxs-lookup"><span data-stu-id="110da-119">Letter, Other</span></span>                 |
| <span data-ttu-id="110da-120">Mn</span><span class="sxs-lookup"><span data-stu-id="110da-120">Mn</span></span>                 | <span data-ttu-id="110da-121">Označit, nemezery</span><span class="sxs-lookup"><span data-stu-id="110da-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="110da-122">Mc</span><span class="sxs-lookup"><span data-stu-id="110da-122">Mc</span></span>                 | <span data-ttu-id="110da-123">značka, kombinování mezer</span><span class="sxs-lookup"><span data-stu-id="110da-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="110da-124">Nd</span><span class="sxs-lookup"><span data-stu-id="110da-124">Nd</span></span>                 | <span data-ttu-id="110da-125">Číslo, desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="110da-125">Number, Decimal</span></span>               |
| <span data-ttu-id="110da-126">Nl</span><span class="sxs-lookup"><span data-stu-id="110da-126">Nl</span></span>                 | <span data-ttu-id="110da-127">číslo, písmeno</span><span class="sxs-lookup"><span data-stu-id="110da-127">Number, Letter</span></span>                |

<span data-ttu-id="110da-128">XAML definuje druhou gramatiku DottedXamlName, která se používá pro odkazy na vlastnosti a události a také pro připojené členy.</span><span class="sxs-lookup"><span data-stu-id="110da-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="110da-129">Další informace naleznete <xref:System.Windows.DependencyProperty> v tématu a [Přehled XAML (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="110da-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="110da-130">Řetězcové hodnoty typu DottedXamlName musí odpovídat následující gramatice:</span><span class="sxs-lookup"><span data-stu-id="110da-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="110da-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="110da-131">Remarks</span></span>

<span data-ttu-id="110da-132">Kompletní specifikaci naleznete v tématu [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="110da-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
