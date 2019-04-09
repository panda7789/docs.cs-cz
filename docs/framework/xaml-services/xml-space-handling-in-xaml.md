---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193314"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="249b7-102">Práce s atributem xml:space v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="249b7-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="249b7-103">`xml:space` Atribut je atribut definice XML, který deklaruje chování operací zpracování prázdných znaků v rámci elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="249b7-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="249b7-104">Toto chování platí pro veškerý obsah (vnitřní text) obsažené v rámci elementu kde `xml:space` je deklarován a také rozsahy pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="249b7-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="249b7-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="249b7-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="249b7-106">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="249b7-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="249b7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="249b7-107">Remarks</span></span>  
 <span data-ttu-id="249b7-108">Definice `xml:space` atribut v XAML, včetně jeho dvě možné hodnoty pochází z `xml:space` definované jako "speciální atribut" specifikaci W3C pro XML.</span><span class="sxs-lookup"><span data-stu-id="249b7-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="249b7-109">Výchozí hodnota `xml:space` atribut je hodnota literálu `"default"`.</span><span class="sxs-lookup"><span data-stu-id="249b7-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="249b7-110">Pro hodnotu `"default"`, nebo pokud `xml:space` není vůbec, uvedené chování významné parsování prázdné místo je výchozí zpracování, jak je definováno v tématu [– zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="249b7-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="249b7-111">Chcete-li zachovat mezer v obsahu elementu objektu, zadejte `xml:space="preserve"` u tohoto elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="249b7-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="249b7-112">V části většiny interpretace `xml:space` efekty atribut a hodnota atributu oborem pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="249b7-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="249b7-113">Úplné informace o – zpracování mezerových znaků v XAML najdete v části [– zpracování mezerových znaků v XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="249b7-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="249b7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="249b7-114">See also</span></span>

- [<span data-ttu-id="249b7-115">Zpracování prázdných znaků v jazyku XAML</span><span class="sxs-lookup"><span data-stu-id="249b7-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="249b7-116">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="249b7-116">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
