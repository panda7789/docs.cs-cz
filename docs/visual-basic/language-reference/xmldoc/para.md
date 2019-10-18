---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524736"
---
# <a name="para-visual-basic"></a><span data-ttu-id="a1341-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1341-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="a1341-103">Určuje, že obsah je formátován jako odstavec.</span><span class="sxs-lookup"><span data-stu-id="a1341-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1341-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1341-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1341-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="a1341-106">Text odstavce</span><span class="sxs-lookup"><span data-stu-id="a1341-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1341-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1341-107">Remarks</span></span>  
 <span data-ttu-id="a1341-108">Značka `<para>` je určena pro použití uvnitř značky, jako je například [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)nebo [\<returns >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidat do textu strukturu.</span><span class="sxs-lookup"><span data-stu-id="a1341-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="a1341-109">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="a1341-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1341-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1341-110">Example</span></span>  
 <span data-ttu-id="a1341-111">V tomto příkladu se používá značka `<para>` k rozdělení oddílu poznámky pro metodu `UpdateRecord` na dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="a1341-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a1341-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1341-112">See also</span></span>

- [<span data-ttu-id="a1341-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="a1341-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
