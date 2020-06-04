---
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 5999a4ebcc90f21ee8331b96ffb2a50f7905b1b6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411509"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="5695f-101">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5695f-101">\<seealso> (Visual Basic)</span></span>
<span data-ttu-id="5695f-102">Určuje odkaz, který se zobrazí v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="5695f-102">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5695f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5695f-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5695f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5695f-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="5695f-105">Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="5695f-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="5695f-106">Kompilátor kontroluje, zda daný prvek kódu existuje a zda předává `member` do názvu prvku ve výstupním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5695f-106">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="5695f-107">`member`v uvozovkách ("") se musí vyskytovat.</span><span class="sxs-lookup"><span data-stu-id="5695f-107">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5695f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5695f-108">Remarks</span></span>  
 <span data-ttu-id="5695f-109">Použijte `<seealso>` značku k určení textu, který se má zobrazit v části Viz také.</span><span class="sxs-lookup"><span data-stu-id="5695f-109">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="5695f-110">Slouží [\<see>](see.md) k zadání odkazu z textu.</span><span class="sxs-lookup"><span data-stu-id="5695f-110">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="5695f-111">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="5695f-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5695f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5695f-112">Example</span></span>  
 <span data-ttu-id="5695f-113">Tento příklad používá `<seealso>` značku v `DoesRecordExist` oddílu poznámky pro odkaz na `UpdateRecord` metodu.</span><span class="sxs-lookup"><span data-stu-id="5695f-113">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5695f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5695f-114">See also</span></span>

- [<span data-ttu-id="5695f-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="5695f-115">XML Comment Tags</span></span>](index.md)
