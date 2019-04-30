---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774813"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="84b00-102">Hodnotu typu 'type1' nelze převést na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="84b00-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="84b00-103">Nelze převést hodnotu typu 'type1' na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="84b00-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="84b00-104">Vlastnost 'Value' slouží k získání řetězcové hodnoty prvního prvku řetězce "\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="84b00-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="84b00-105">Byl proveden pokus o implicitně přetypován na určitý typ literálu XML.</span><span class="sxs-lookup"><span data-stu-id="84b00-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="84b00-106">Literál XML nelze přetypovat na zadaný typ implicitně.</span><span class="sxs-lookup"><span data-stu-id="84b00-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="84b00-107">**ID chyby:** BC31194</span><span class="sxs-lookup"><span data-stu-id="84b00-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84b00-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="84b00-108">To correct this error</span></span>  
  
- <span data-ttu-id="84b00-109">Použití `Value` vlastnost tak, aby odkazovaly na jeho hodnotu jako literál XML `String`.</span><span class="sxs-lookup"><span data-stu-id="84b00-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="84b00-110">Použití `CType` funkce, jiné funkce pro převod typu, nebo <xref:System.Convert> k přetypování hodnoty jako zadaný typ třídy.</span><span class="sxs-lookup"><span data-stu-id="84b00-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b00-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84b00-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="84b00-112">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="84b00-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="84b00-113">Literály XML</span><span class="sxs-lookup"><span data-stu-id="84b00-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="84b00-114">XML</span><span class="sxs-lookup"><span data-stu-id="84b00-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
