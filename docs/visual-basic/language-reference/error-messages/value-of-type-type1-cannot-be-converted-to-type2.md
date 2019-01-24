---
title: Hodnotu typu &#39;type1&#39; nelze převést na &#39;typ2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 657e0feb675e15b9ece00d40c3d1ebe932a29099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568283"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="9a386-102">Hodnotu typu &#39;type1&#39; nelze převést na &#39;typ2&#39;</span><span class="sxs-lookup"><span data-stu-id="9a386-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="9a386-103">Nelze převést hodnotu typu 'type1' na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="9a386-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="9a386-104">Vlastnost 'Value' slouží k získání řetězcové hodnoty prvního prvku řetězce "\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="9a386-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="9a386-105">Byl proveden pokus o implicitně přetypován na určitý typ literálu XML.</span><span class="sxs-lookup"><span data-stu-id="9a386-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="9a386-106">Literál XML nelze přetypovat na zadaný typ implicitně.</span><span class="sxs-lookup"><span data-stu-id="9a386-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="9a386-107">**ID chyby:** BC31194</span><span class="sxs-lookup"><span data-stu-id="9a386-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a386-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9a386-108">To correct this error</span></span>  
  
-   <span data-ttu-id="9a386-109">Použití `Value` vlastnost tak, aby odkazovaly na jeho hodnotu jako literál XML `String`.</span><span class="sxs-lookup"><span data-stu-id="9a386-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="9a386-110">Použití `CType` funkce, jiné funkce pro převod typu, nebo <xref:System.Convert> k přetypování hodnoty jako zadaný typ třídy.</span><span class="sxs-lookup"><span data-stu-id="9a386-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a386-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a386-111">See also</span></span>
- <xref:System.Convert>
- [<span data-ttu-id="9a386-112">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="9a386-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9a386-113">Literály XML</span><span class="sxs-lookup"><span data-stu-id="9a386-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="9a386-114">XML</span><span class="sxs-lookup"><span data-stu-id="9a386-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
