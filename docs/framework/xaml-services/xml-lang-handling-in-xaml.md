---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b3f236b2378d6af78f034856e3ba0f7a9e17993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837139"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="a476e-102">Práce s atributem xml:lang v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="a476e-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="a476e-103">Atribut `xml:lang` je atribut definovaný v jazyce XML, který deklaruje informace o jazyku a jazykové verzi elementu v jazyce XML.</span><span class="sxs-lookup"><span data-stu-id="a476e-103">The `xml:lang` attribute is an XML-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="a476e-104">Stejný význam atributu v jazyce XAML přetrvává; platí však některé další požadavky.</span><span class="sxs-lookup"><span data-stu-id="a476e-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="a476e-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="a476e-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="a476e-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="a476e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a476e-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="a476e-107">*rfc3066lang*</span></span>|<span data-ttu-id="a476e-108">Řetězec, který je odvozen z standardu [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) a označuje jazyk nebo jazykovou oblast.</span><span class="sxs-lookup"><span data-stu-id="a476e-108">A string that is derived from the [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="a476e-109">Pokud se jedná o druhý, jazyk a oblast jsou oddělené jedním spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="a476e-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="a476e-110">Další informace o hodnotách a formátu najdete v tématu <xref:System.Windows.Markup.XmlLanguage>.</span><span class="sxs-lookup"><span data-stu-id="a476e-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a476e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a476e-111">Remarks</span></span>  
 <span data-ttu-id="a476e-112">Definice atributu `xml:lang` v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozena z `xml:lang` definovaná jako "speciální atribut" konsorcium World Wide Web (W3C) pro XML.</span><span class="sxs-lookup"><span data-stu-id="a476e-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the World Wide Web Consortium (W3C) for XML.</span></span> <span data-ttu-id="a476e-113">Informace o jazyku a jazykové verzi jsou potenciálně zpracovávány různými způsoby podle prvků v závislosti na jejich implementacích. Neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování atributu `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="a476e-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="a476e-114">Výchozí hodnota atributu `xml:lang` je prázdný řetězec na úrovni atributu.</span><span class="sxs-lookup"><span data-stu-id="a476e-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="a476e-115">Vliv atributů `xml:lang` a hodnota atributu jsou obecně perpetuated na podřízené prvky, pokud jsou interpretovány systémy, které pracují s hodnotami `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="a476e-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="a476e-116">Při interpretaci autory XAML .NET Frameworkch služeb XAML může `xml:lang` hodnotu vytvořit <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v reprezentaci podkladových objektů; Toto chování je však závislé na tom, zda je hodnota zadaná pro `xml:lang` platnou konstrukcí pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="a476e-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="a476e-117">Rozhraní můžou vytvořit přidružení mezi vlastnostmi definovanými rozhraním a významem `xml:lang` v XML, a to použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a476e-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="a476e-118">Uzly použití WPF</span><span class="sxs-lookup"><span data-stu-id="a476e-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="a476e-119">Pro prvky, které jsou odvozeny třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, lze namísto atributu `xml:lang` použít ekvivalentní vlastnost Dependency <xref:System.Windows.FrameworkElement.Language%2A>.</span><span class="sxs-lookup"><span data-stu-id="a476e-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="a476e-120">Ve výchozím nastavení vlastnost <xref:System.Windows.FrameworkElement.Language%2A> používá "en-US", pokud není jinak nastavena, buď prostřednictvím vlastnosti, nebo prostřednictvím zpracování atributu `xml:lang`.</span><span class="sxs-lookup"><span data-stu-id="a476e-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a476e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a476e-121">See also</span></span>

- [<span data-ttu-id="a476e-122">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="a476e-122">Globalization for WPF</span></span>](../wpf/advanced/globalization-for-wpf.md)
