---
title: Hodnotu typu 'type1' nelze převést na 'type2'.
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400276"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="52b92-102">Hodnotu typu 'type1' nelze převést na 'type2'.</span><span class="sxs-lookup"><span data-stu-id="52b92-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="52b92-103">Hodnotu typu typ1 nelze převést na typ typ2.</span><span class="sxs-lookup"><span data-stu-id="52b92-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="52b92-104">Vlastnost Value lze použít k získání řetězcové hodnoty prvního prvku \<parentElement> .</span><span class="sxs-lookup"><span data-stu-id="52b92-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="52b92-105">Byl proveden pokus o implicitní přetypování literálu XML na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="52b92-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="52b92-106">Literál XML nelze implicitně přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="52b92-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="52b92-107">**ID chyby:** BC31194</span><span class="sxs-lookup"><span data-stu-id="52b92-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52b92-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="52b92-108">To correct this error</span></span>  
  
- <span data-ttu-id="52b92-109">Použijte `Value` vlastnost literálu XML pro odkaz na svou hodnotu jako `String` .</span><span class="sxs-lookup"><span data-stu-id="52b92-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="52b92-110">Použijte `CType` funkci, jinou funkci konverze typu nebo <xref:System.Convert> třídu pro přetypování hodnoty jako zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="52b92-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b92-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="52b92-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="52b92-112">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="52b92-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="52b92-113">Literály XML</span><span class="sxs-lookup"><span data-stu-id="52b92-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="52b92-114">XML</span><span class="sxs-lookup"><span data-stu-id="52b92-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
