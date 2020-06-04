---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 380923c2313450afc5745b25eeea6a444705dd3f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411522"
---
# <a name="see-visual-basic"></a><span data-ttu-id="a6885-101">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6885-101">\<see> (Visual Basic)</span></span>
<span data-ttu-id="a6885-102">Určuje odkaz na jiného člena.</span><span class="sxs-lookup"><span data-stu-id="a6885-102">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6885-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6885-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6885-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6885-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="a6885-105">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="a6885-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="a6885-106">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="a6885-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="a6885-107">`member`v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="a6885-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6885-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6885-108">Remarks</span></span>  
 <span data-ttu-id="a6885-109">Pomocí `<see>` značky můžete zadat odkaz v rámci textu.</span><span class="sxs-lookup"><span data-stu-id="a6885-109">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="a6885-110">Slouží [\<seealso>](seealso.md) k označení textu, který se může objevit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="a6885-110">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="a6885-111">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="a6885-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6885-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6885-112">Example</span></span>  
 <span data-ttu-id="a6885-113">Tento příklad používá `<see>` značku v `UpdateRecord` oddílu poznámky pro odkaz na `DoesRecordExist` metodu.</span><span class="sxs-lookup"><span data-stu-id="a6885-113">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a6885-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6885-114">See also</span></span>

- [<span data-ttu-id="a6885-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a6885-115">XML Comment Tags</span></span>](index.md)
