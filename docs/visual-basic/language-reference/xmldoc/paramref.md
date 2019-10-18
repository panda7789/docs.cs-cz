---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 85171bd8deeb5f54c4560bb8b2339107bb8d8c68
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524709"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="9d548-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d548-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="9d548-103">Zformátuje slovo jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9d548-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d548-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d548-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d548-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d548-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9d548-106">Název parametru, na který se má odkazovat</span><span class="sxs-lookup"><span data-stu-id="9d548-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="9d548-107">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9d548-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d548-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d548-108">Remarks</span></span>  
 <span data-ttu-id="9d548-109">Značka `<paramref>` poskytuje způsob, jak označit, že slovo je parametrem.</span><span class="sxs-lookup"><span data-stu-id="9d548-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="9d548-110">Soubor XML může být zpracován pro naformátování tohoto parametru nějakým odlišným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9d548-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="9d548-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="9d548-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d548-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d548-112">Example</span></span>  
 <span data-ttu-id="9d548-113">Tento příklad používá značku `<paramref>` pro odkazování na parametr `id`.</span><span class="sxs-lookup"><span data-stu-id="9d548-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9d548-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d548-114">See also</span></span>

- [<span data-ttu-id="9d548-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9d548-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
