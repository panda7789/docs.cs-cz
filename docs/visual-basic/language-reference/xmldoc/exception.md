---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346962"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="58dc9-101">> \<výjimky (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58dc9-101">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="58dc9-102">Určuje, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="58dc9-102">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58dc9-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58dc9-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="58dc9-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="58dc9-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="58dc9-105">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="58dc9-105">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="58dc9-106">Kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="58dc9-106">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="58dc9-107">`member` musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="58dc9-107">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="58dc9-108">Popis.</span><span class="sxs-lookup"><span data-stu-id="58dc9-108">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58dc9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58dc9-109">Remarks</span></span>  
 <span data-ttu-id="58dc9-110">Pomocí značky `<exception>` určete, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="58dc9-110">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="58dc9-111">Tato značka se aplikuje na definici metody.</span><span class="sxs-lookup"><span data-stu-id="58dc9-111">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="58dc9-112">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="58dc9-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58dc9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="58dc9-113">Example</span></span>  
 <span data-ttu-id="58dc9-114">V tomto příkladu se používá značka `<exception>` k popisu výjimky, kterou může funkce `IntDivide` vyvolat.</span><span class="sxs-lookup"><span data-stu-id="58dc9-114">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="58dc9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58dc9-115">See also</span></span>

- [<span data-ttu-id="58dc9-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="58dc9-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
