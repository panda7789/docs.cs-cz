---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071442"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="ae637-102">Práce s atributem xml:lang v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="ae637-102">xml:lang Handling in XAML</span></span>

<span data-ttu-id="ae637-103">Atribut `xml:lang` je atribut definovaný jazykem XML, který deklaruje informace o jazyce a jazykové verzi pro prvek ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="ae637-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="ae637-104">Stejný význam atributu přetrvává v XAML; platí však některé další aspekty.</span><span class="sxs-lookup"><span data-stu-id="ae637-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="ae637-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="ae637-105">XAML Attribute Usage</span></span>

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a><span data-ttu-id="ae637-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="ae637-106">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="ae637-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="ae637-107">*rfc3066lang*</span></span>|<span data-ttu-id="ae637-108">Řetězec, který je odvozen ze standardu [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) a identifikuje jazyk nebo jazykovou oblast.</span><span class="sxs-lookup"><span data-stu-id="ae637-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="ae637-109">Pokud je to druhé, jazyk a oblast jsou odděleny jedním pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="ae637-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="ae637-110">Další <xref:System.Windows.Markup.XmlLanguage> informace o hodnotách a formátu naleznete v tématu.</span><span class="sxs-lookup"><span data-stu-id="ae637-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae637-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae637-111">Remarks</span></span>

<span data-ttu-id="ae637-112">Definice atributu `xml:lang` v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozena od definovaného `xml:lang` jako "zvláštní atribut" konsorciem W3C (World Wide Web Consortium) pro JAZYK XML.</span><span class="sxs-lookup"><span data-stu-id="ae637-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="ae637-113">Informace o jazyce a jazykové verzi jsou potenciálně zpracovávány různými způsoby prvky v závislosti na jejich implementaci; však neexistuje žádné [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] výchozí `xml:lang` zpracování atributu.</span><span class="sxs-lookup"><span data-stu-id="ae637-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>

<span data-ttu-id="ae637-114">Výchozí hodnota atributu `xml:lang` je prázdný řetězec na úrovni atributu.</span><span class="sxs-lookup"><span data-stu-id="ae637-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>

<span data-ttu-id="ae637-115">Atribut `xml:lang` účinky a hodnota atributu jsou obecně udržovat podřízené prvky, při interpretaci systémy, které působí na `xml:lang` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae637-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>

<span data-ttu-id="ae637-116">Při interpretaci autory XAML služby .NET `xml:lang` XAML Services může hodnota vytvořit <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v reprezentaci podkladového objektu; však toto chování závisí na `xml:lang` tom, zda je zadaná hodnota pro platné konstrukce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="ae637-116">When interpreted by XAML writers of .NET XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>

<span data-ttu-id="ae637-117">Architektury můžete vytvořit přidružení mezi vlastnostmi definované `xml:lang` v rámci <xref:System.Windows.Markup.XmlLangPropertyAttribute> a význam v xml použitím na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae637-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>

## <a name="wpf-usage-nodes"></a><span data-ttu-id="ae637-118">Uzly využití WPF</span><span class="sxs-lookup"><span data-stu-id="ae637-118">WPF Usage Nodes</span></span>

<span data-ttu-id="ae637-119">Pro prvky, které <xref:System.Windows.FrameworkElement> jsou <xref:System.Windows.FrameworkContentElement>odvozené třídy <xref:System.Windows.FrameworkElement.Language%2A> nebo , můžete `xml:lang` použít ekvivalentní závislost vlastnost namísto atributu.</span><span class="sxs-lookup"><span data-stu-id="ae637-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="ae637-120">Ve výchozím <xref:System.Windows.FrameworkElement.Language%2A> nastavení vlastnost používá "en US", pokud není jinak nastavena, `xml:lang` buď prostřednictvím vlastnosti, nebo zpracováním atributu.</span><span class="sxs-lookup"><span data-stu-id="ae637-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae637-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae637-121">See also</span></span>

- [<span data-ttu-id="ae637-122">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="ae637-122">Globalization for WPF</span></span>](../../framework/wpf/advanced/globalization-for-wpf.md)
