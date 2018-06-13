---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: af971ad9ea74e123b939ff8d8488e4e45c5d4aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563464"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="b91e5-102">Práce s atributem xml:space v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="b91e5-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="b91e5-103">`xml:space` Se atribut definované XML, který deklaruje chování významný mezerový znak zpracování v rámci elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="b91e5-103">The `xml:space` attribute is an XML-defined attribute that declares the significant whitespace processing behavior within an object element.</span></span> <span data-ttu-id="b91e5-104">Toto chování je relevantní pro veškerý obsah (vnitřní text) obsažených v elementu kde `xml:space` je deklarován a také rozsahy pro podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="b91e5-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b91e5-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="b91e5-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="b91e5-106">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="b91e5-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="b91e5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b91e5-107">Remarks</span></span>  
 <span data-ttu-id="b91e5-108">Definice pro `xml:space` atribut v jazyce XAML, včetně jeho dvě možné hodnoty je odvozený od `xml:space` podle definice jako "speciální atribut" W3C specifikace XML.</span><span class="sxs-lookup"><span data-stu-id="b91e5-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="b91e5-109">Výchozí hodnota `xml:space` atribut je literálovou hodnotou `"default"`.</span><span class="sxs-lookup"><span data-stu-id="b91e5-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="b91e5-110">Pro hodnotu `"default"`, nebo pokud `xml:space` není uvedené ve všech chování analýza významný mezerový znak je výchozí zpracování, jak jsou definovány v sekci [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b91e5-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant whitespace parsing is the default handling, as defined in the topic [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="b91e5-111">Pokud chcete zachovat prázdných znaků v obsahu elementu objektu, zadejte `xml:space="preserve"` u tohoto objektu elementu.</span><span class="sxs-lookup"><span data-stu-id="b91e5-111">To preserve whitespace within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="b91e5-112">V části většiny interpretace `xml:space` atribut dopady a hodnota atributu je v oboru podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="b91e5-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="b91e5-113">Úplné informace o zpracování prázdných znaků v jazyce XAML, najdete v části [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b91e5-113">For a complete discussion of whitespace processing in XAML, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91e5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b91e5-114">See Also</span></span>  
 [<span data-ttu-id="b91e5-115">Zpracování prázdných znaků v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="b91e5-115">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="b91e5-116">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="b91e5-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
