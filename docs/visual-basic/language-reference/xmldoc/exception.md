---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 16ffb4f6b57dabb3650376c913a7d7608a00646d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523931"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="6eb35-102">\<exception > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6eb35-102">\<exception> (Visual Basic)</span></span>
<span data-ttu-id="6eb35-103">Určuje, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="6eb35-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb35-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eb35-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="6eb35-106">Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace.</span><span class="sxs-lookup"><span data-stu-id="6eb35-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="6eb35-107">Kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="6eb35-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="6eb35-108">`member` musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="6eb35-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="6eb35-109">Popis.</span><span class="sxs-lookup"><span data-stu-id="6eb35-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb35-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eb35-110">Remarks</span></span>  
 <span data-ttu-id="6eb35-111">Pomocí značky `<exception>` určete, které výjimky mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="6eb35-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="6eb35-112">Tato značka se aplikuje na definici metody.</span><span class="sxs-lookup"><span data-stu-id="6eb35-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="6eb35-113">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="6eb35-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eb35-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6eb35-114">Example</span></span>  
 <span data-ttu-id="6eb35-115">V tomto příkladu se používá značka `<exception>` k popisu výjimky, kterou může funkce `IntDivide` vyvolat.</span><span class="sxs-lookup"><span data-stu-id="6eb35-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6eb35-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eb35-116">See also</span></span>

- [<span data-ttu-id="6eb35-117">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6eb35-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
