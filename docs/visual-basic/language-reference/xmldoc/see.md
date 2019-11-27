---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352232"
---
# <a name="see-visual-basic"></a><span data-ttu-id="2573e-101">\<Zobrazit > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2573e-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="2573e-102">Určuje odkaz na jiného člena.</span><span class="sxs-lookup"><span data-stu-id="2573e-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2573e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2573e-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2573e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="2573e-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="2573e-105">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="2573e-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2573e-106">Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` k názvu elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2573e-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="2573e-107">`member` musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="2573e-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2573e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2573e-108">Remarks</span></span>  
 <span data-ttu-id="2573e-109">Pomocí značky `<see>` můžete zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="2573e-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="2573e-110">Pomocí [\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) označte text, který se může objevit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="2573e-110">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="2573e-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="2573e-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2573e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2573e-112">Example</span></span>  
 <span data-ttu-id="2573e-113">Tento příklad používá značku `<see>` v části `UpdateRecord` poznámky pro odkaz na metodu `DoesRecordExist`.</span><span class="sxs-lookup"><span data-stu-id="2573e-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2573e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2573e-114">See also</span></span>

- [<span data-ttu-id="2573e-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="2573e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
