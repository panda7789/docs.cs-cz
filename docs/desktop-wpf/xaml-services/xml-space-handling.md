---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071435"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="24136-102">Práce s atributem xml:space v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="24136-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="24136-103">Atribut `xml:space` je atribut definovaný jazykem XML, který deklaruje významné chování zpracování prázdného místa v rámci elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="24136-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="24136-104">Toto chování je relevantní pro veškerý obsah (vnitřní `xml:space` text) obsažené v elementu, kde je deklarována a také obory podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="24136-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="24136-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="24136-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="24136-106">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="24136-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="24136-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24136-107">Remarks</span></span>

<span data-ttu-id="24136-108">Definice atributu `xml:space` v XAML včetně jeho dvou možných hodnot je odvozena od `xml:space` definovaného jako "speciální atribut" specifikacemi W3C pro XML.</span><span class="sxs-lookup"><span data-stu-id="24136-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="24136-109">Výchozí hodnota atributu `xml:space` je hodnota `"default"`literálu .</span><span class="sxs-lookup"><span data-stu-id="24136-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="24136-110">Pro hodnotu `"default"`, `xml:space` nebo pokud není uvedeno vůbec, chování významné prázdné místo analýzy je výchozí zpracování, jak je definováno v tématu [zpracování prázdnémísto v XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="24136-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="24136-111">Chcete-li zachovat prázdné místo `xml:space="preserve"` v obsahu prvku objektu, zadejte na tomto prvku objektu.</span><span class="sxs-lookup"><span data-stu-id="24136-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="24136-112">Při většině interpretací `xml:space` jsou efekty atributů a hodnota atributu vymezeny na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="24136-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="24136-113">Úplnou diskusi o zpracování prázdného místa v XAML naleznete [v tématu Zpracování prázdného místa v XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="24136-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24136-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="24136-114">See also</span></span>

- [<span data-ttu-id="24136-115">Zpracování prázdných znaků v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="24136-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="24136-116">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="24136-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
