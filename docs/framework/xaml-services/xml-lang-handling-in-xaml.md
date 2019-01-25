---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 508c1151b1b196a84b7c3a576e18d10c0a706fad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692393"
---
# <a name="xmllang-handling-in-xaml"></a><span data-ttu-id="9df5c-102">Práce s atributem xml:lang v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="9df5c-102">xml:lang Handling in XAML</span></span>
<span data-ttu-id="9df5c-103">`xml:lang` Atribut je [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-definovaný atribut, který deklaruje informace o jazyk a jazykovou verzi pro element v XML.</span><span class="sxs-lookup"><span data-stu-id="9df5c-103">The `xml:lang` attribute is an [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-defined attribute that declares the language and culture information for an element in XML.</span></span> <span data-ttu-id="9df5c-104">Tento stejný význam atributu přetrvává v XAML; však použít několik dalších důležitých informací.</span><span class="sxs-lookup"><span data-stu-id="9df5c-104">This same meaning of the attribute persists in XAML; however, some additional considerations apply.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9df5c-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="9df5c-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="9df5c-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="9df5c-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9df5c-107">*rfc3066lang*</span><span class="sxs-lookup"><span data-stu-id="9df5c-107">*rfc3066lang*</span></span>|<span data-ttu-id="9df5c-108">Řetězec, který je odvozen z [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standardní a identifikuje jazyka nebo jazyka oblasti.</span><span class="sxs-lookup"><span data-stu-id="9df5c-108">A string that is derived from the [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standard and identifies either a language or a language-region.</span></span> <span data-ttu-id="9df5c-109">Pokud je to ten, jazyka a oblasti jsou oddělené pomlčkou jeden.</span><span class="sxs-lookup"><span data-stu-id="9df5c-109">When it is the latter, the language and region are separated by a single hyphen.</span></span> <span data-ttu-id="9df5c-110">Zobrazit <xref:System.Windows.Markup.XmlLanguage> Další informace o hodnotách a formát.</span><span class="sxs-lookup"><span data-stu-id="9df5c-110">See <xref:System.Windows.Markup.XmlLanguage> for more information about the values and format.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9df5c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9df5c-111">Remarks</span></span>  
 <span data-ttu-id="9df5c-112">Definice `xml:lang` atribut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozen z `xml:lang` definované jako "speciální atribut" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] pro [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9df5c-112">The definition for the `xml:lang` attribute in [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] is derived from `xml:lang` as defined as a "special attribute" by the [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] for [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)].</span></span> <span data-ttu-id="9df5c-113">Informace o jazyk a jazykovou verzi potenciálně zpracovává různými způsoby prvků, v závislosti na jejich implementace; neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="9df5c-113">Language and culture information is potentially processed in different ways by elements, depending on their implementations; however, there is no default [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing of the `xml:lang` attribute.</span></span>  
  
 <span data-ttu-id="9df5c-114">Výchozí hodnota `xml:lang` atributu je prázdný řetězec na úrovni atribut.</span><span class="sxs-lookup"><span data-stu-id="9df5c-114">The default value of the `xml:lang` attribute is an empty string at the attribute level.</span></span>  
  
 <span data-ttu-id="9df5c-115">`xml:lang` Efekty atribut a hodnota atributu jsou obecně perpetuated pro podřízené prvky, když jsou interpretovány systémy, které působí na `xml:lang` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9df5c-115">The `xml:lang` attribute effects and the value of the attribute are generally perpetuated to child elements, when interpreted by systems that act on `xml:lang` values.</span></span>  
  
 <span data-ttu-id="9df5c-116">Když interpretovat XAML zapisovače rozhraní .NET Framework XAML Services `xml:lang` může vytvořit hodnotu <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> reprezentace objektů v základním objektu, ale toto chování závisí na tom, zda hodnota zadaná pro omezení `xml:lang`je platná konstrukce pro tyto třídy.</span><span class="sxs-lookup"><span data-stu-id="9df5c-116">When interpreted by XAML writers of .NET Framework XAML Services, an `xml:lang` value can create <xref:System.Windows.Markup.XmlLanguage> or <xref:System.Globalization.CultureInfo> objects in the underlying object representation; however, that behavior depends on whether the value specified for `xml:lang` is a valid construction for those classes.</span></span>  
  
 <span data-ttu-id="9df5c-117">Rozhraní může vytvořit přidružení mezi vlastnosti definované v rámci rozhraní a význam `xml:lang` ve formátu XML použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9df5c-117">Frameworks can create associations between framework-defined properties and the meaning of `xml:lang` in XML by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> to the property.</span></span>  
  
## <a name="wpf-usage-nodes"></a><span data-ttu-id="9df5c-118">Využití uzlů WPF</span><span class="sxs-lookup"><span data-stu-id="9df5c-118">WPF Usage Nodes</span></span>  
 <span data-ttu-id="9df5c-119">Pro prvky, které jsou odvozené třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, můžete ekvivalentní <xref:System.Windows.FrameworkElement.Language%2A> vlastnost závislosti místo `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="9df5c-119">For elements that are derived classes of <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement>, you can use the equivalent <xref:System.Windows.FrameworkElement.Language%2A> dependency property instead of the `xml:lang` attribute.</span></span> <span data-ttu-id="9df5c-120">Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Language%2A> vlastnost používá "en US", pokud není jinak nastavena, prostřednictvím vlastnosti nebo prostřednictvím zpracování `xml:lang` atribut.</span><span class="sxs-lookup"><span data-stu-id="9df5c-120">By default, the <xref:System.Windows.FrameworkElement.Language%2A> property uses "en-US" if it is not otherwise set, either through the property or through processing the `xml:lang` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df5c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9df5c-121">See also</span></span>
- [<span data-ttu-id="9df5c-122">Globalizace pro WPF</span><span class="sxs-lookup"><span data-stu-id="9df5c-122">Globalization for WPF</span></span>](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
