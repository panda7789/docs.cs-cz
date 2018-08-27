---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 051cb6b3a314509e9593ee570fd659098670e88b
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925854"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="f79e8-102">Práce s atributem xml:space v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="f79e8-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="f79e8-103">`xml:space` Atribut je atribut definice XML, který deklaruje chování operací zpracování prázdných znaků v rámci elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="f79e8-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="f79e8-104">Toto chování platí pro veškerý obsah (vnitřní text) obsažené v rámci elementu kde `xml:space` je deklarován a také rozsahy pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="f79e8-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f79e8-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="f79e8-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="f79e8-106">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="f79e8-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="f79e8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f79e8-107">Remarks</span></span>  
 <span data-ttu-id="f79e8-108">Definice `xml:space` atribut v XAML, včetně jeho dvě možné hodnoty pochází z `xml:space` definované jako "speciální atribut" specifikaci W3C pro XML.</span><span class="sxs-lookup"><span data-stu-id="f79e8-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="f79e8-109">Výchozí hodnota `xml:space` atribut je hodnota literálu `"default"`.</span><span class="sxs-lookup"><span data-stu-id="f79e8-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="f79e8-110">Pro hodnotu `"default"`, nebo pokud `xml:space` není vůbec, uvedené chování významné parsování prázdné místo je výchozí zpracování, jak je definováno v tématu [– zpracování mezerových znaků v XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f79e8-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="f79e8-111">Chcete-li zachovat mezer v obsahu elementu objektu, zadejte `xml:space="preserve"` u tohoto elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="f79e8-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="f79e8-112">V části většiny interpretace `xml:space` efekty atribut a hodnota atributu oborem pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="f79e8-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="f79e8-113">Úplné informace o – zpracování mezerových znaků v XAML najdete v části [– zpracování mezerových znaků v XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="f79e8-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79e8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f79e8-114">See Also</span></span>  
 [<span data-ttu-id="f79e8-115">Zpracování mezerových znaků v XAML</span><span class="sxs-lookup"><span data-stu-id="f79e8-115">White-space processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="f79e8-116">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f79e8-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
