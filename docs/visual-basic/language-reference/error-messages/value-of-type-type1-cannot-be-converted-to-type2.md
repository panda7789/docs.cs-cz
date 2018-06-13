---
title: Hodnotu typu &#39;type1&#39; nelze převést na &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602752"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="ab8d4-102">Hodnotu typu &#39;type1&#39; nelze převést na &#39;type2&#39;</span><span class="sxs-lookup"><span data-stu-id="ab8d4-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="ab8d4-103">Hodnotu typu 'type1' nelze převést na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="ab8d4-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="ab8d4-104">Vlastnost 'Hodnota' můžete získat hodnotu řetězce první prvek '\<parentElement > ".</span><span class="sxs-lookup"><span data-stu-id="ab8d4-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="ab8d4-105">Byl proveden pokus o implicitně převést literál na určitý typ XML.</span><span class="sxs-lookup"><span data-stu-id="ab8d4-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="ab8d4-106">Literál XML nelze implicitně převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="ab8d4-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="ab8d4-107">**ID chyby:** BC31194</span><span class="sxs-lookup"><span data-stu-id="ab8d4-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab8d4-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ab8d4-108">To correct this error</span></span>  
  
-   <span data-ttu-id="ab8d4-109">Použití `Value` vlastnost literál XML tak, aby odkazovaly jako jeho hodnotu `String`.</span><span class="sxs-lookup"><span data-stu-id="ab8d4-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="ab8d4-110">Použití `CType` funkce, funkce Převod jiného typu, nebo <xref:System.Convert> třída přetypovat na hodnotu jako zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="ab8d4-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab8d4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab8d4-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="ab8d4-112">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ab8d4-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ab8d4-113">Literály XML</span><span class="sxs-lookup"><span data-stu-id="ab8d4-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="ab8d4-114">XML</span><span class="sxs-lookup"><span data-stu-id="ab8d4-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
