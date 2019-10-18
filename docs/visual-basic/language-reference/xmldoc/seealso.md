---
title: <seealso> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0231ff748949874f4b477cac15d891d313b25f4f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524648"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="5fe67-102">\<seealso > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fe67-102">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="5fe67-103">Určuje odkaz, který se zobrazí v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="5fe67-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fe67-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fe67-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="5fe67-106">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="5fe67-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="5fe67-107">Kompilátor zkontroluje, zda daný prvek kódu existuje a předá `member` k názvu elementu ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5fe67-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="5fe67-108">`member` musí být v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="5fe67-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fe67-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fe67-109">Remarks</span></span>  
 <span data-ttu-id="5fe67-110">Pomocí značky `<seealso>` můžete zadat text, který se má zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="5fe67-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="5fe67-111">Pomocí [\<see >](../../../visual-basic/language-reference/xmldoc/see.md) zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="5fe67-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="5fe67-112">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="5fe67-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe67-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fe67-113">Example</span></span>  
 <span data-ttu-id="5fe67-114">Tento příklad používá značku `<seealso>` v části `DoesRecordExist` poznámky pro odkaz na metodu `UpdateRecord`.</span><span class="sxs-lookup"><span data-stu-id="5fe67-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe67-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fe67-115">See also</span></span>

- [<span data-ttu-id="5fe67-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="5fe67-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
