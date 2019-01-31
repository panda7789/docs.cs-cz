---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: eb30d63e83452e75f353c44a9d0445c7dbb1013a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287505"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="57ec7-102">Hodnotu typu 'type1' nelze převést na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="57ec7-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="57ec7-103">Nelze převést hodnotu typu 'type1' na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="57ec7-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="57ec7-104">Vlastnost 'Value' slouží k získání řetězcové hodnoty prvního prvku řetězce "\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="57ec7-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="57ec7-105">Byl proveden pokus o implicitně přetypován na určitý typ literálu XML.</span><span class="sxs-lookup"><span data-stu-id="57ec7-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="57ec7-106">Literál XML nelze přetypovat na zadaný typ implicitně.</span><span class="sxs-lookup"><span data-stu-id="57ec7-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="57ec7-107">**ID chyby:** BC31194</span><span class="sxs-lookup"><span data-stu-id="57ec7-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57ec7-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="57ec7-108">To correct this error</span></span>  
  
-   <span data-ttu-id="57ec7-109">Použití `Value` vlastnost tak, aby odkazovaly na jeho hodnotu jako literál XML `String`.</span><span class="sxs-lookup"><span data-stu-id="57ec7-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="57ec7-110">Použití `CType` funkce, jiné funkce pro převod typu, nebo <xref:System.Convert> k přetypování hodnoty jako zadaný typ třídy.</span><span class="sxs-lookup"><span data-stu-id="57ec7-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ec7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57ec7-111">See also</span></span>
- <xref:System.Convert>
- [<span data-ttu-id="57ec7-112">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="57ec7-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="57ec7-113">Literály XML</span><span class="sxs-lookup"><span data-stu-id="57ec7-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="57ec7-114">XML</span><span class="sxs-lookup"><span data-stu-id="57ec7-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
