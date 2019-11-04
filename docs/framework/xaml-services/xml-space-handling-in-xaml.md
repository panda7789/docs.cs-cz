---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458802"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="81114-102">Práce s atributem xml:space v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="81114-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="81114-103">Atribut `xml:space` je atribut definovaný v jazyce XML, který deklaruje významné chování zpracování bílého místa v rámci elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="81114-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="81114-104">Toto chování je relevantní pro veškerý obsah (vnitřní text) obsažený v elementu, kde je `xml:space` deklarována, a také obory pro podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="81114-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="81114-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="81114-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="81114-106">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="81114-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="81114-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81114-107">Remarks</span></span>  
 <span data-ttu-id="81114-108">Definice atributu `xml:space` v jazyce XAML, včetně jeho dvou možných hodnot, je odvozena od `xml:space` definována jako "speciální atribut" specifikacemi W3C Specification for XML.</span><span class="sxs-lookup"><span data-stu-id="81114-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="81114-109">Výchozí hodnota atributu `xml:space` je hodnota literálu `"default"`.</span><span class="sxs-lookup"><span data-stu-id="81114-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="81114-110">V případě hodnoty `"default"`, nebo pokud `xml:space` není uvedena vůbec, je chování významné analýzy bílého místa výchozím zpracováním, jak je definováno v tématu [zpracování prázdných míst v jazyce XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="81114-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="81114-111">Chcete-li zachovat prázdné znaky v obsahu elementu objektu, zadejte `xml:space="preserve"` na tento prvek objektu.</span><span class="sxs-lookup"><span data-stu-id="81114-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="81114-112">V rámci většiny výkladů jsou účinky atributů `xml:space` a hodnota atributu vymezeny na podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="81114-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="81114-113">Úplné informace o zpracování bílého místa v jazyce XAML naleznete v tématu [prázdné místo zpracování v jazyce XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="81114-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81114-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81114-114">See also</span></span>

- [<span data-ttu-id="81114-115">Zpracování prázdných míst v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="81114-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="81114-116">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="81114-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
