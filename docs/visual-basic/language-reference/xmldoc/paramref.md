---
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3ca08016d3cef0c44e4f3c0bd0d017628eda606d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400044"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="3a24b-101">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a24b-101">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="3a24b-102">Zformátuje slovo jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3a24b-102">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a24b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a24b-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a24b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a24b-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3a24b-105">Název parametru, na který se má odkazovat</span><span class="sxs-lookup"><span data-stu-id="3a24b-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="3a24b-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="3a24b-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a24b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a24b-107">Remarks</span></span>  
 <span data-ttu-id="3a24b-108">`<paramref>`Značka poskytuje způsob, jak označit, že je slovo parametr.</span><span class="sxs-lookup"><span data-stu-id="3a24b-108">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="3a24b-109">Soubor XML může být zpracován pro naformátování tohoto parametru nějakým odlišným způsobem.</span><span class="sxs-lookup"><span data-stu-id="3a24b-109">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="3a24b-110">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="3a24b-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a24b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a24b-111">Example</span></span>  
 <span data-ttu-id="3a24b-112">V tomto příkladu se používá `<paramref>` značka pro odkaz na `id` parametr.</span><span class="sxs-lookup"><span data-stu-id="3a24b-112">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3a24b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a24b-113">See also</span></span>

- [<span data-ttu-id="3a24b-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="3a24b-114">XML Comment Tags</span></span>](index.md)
