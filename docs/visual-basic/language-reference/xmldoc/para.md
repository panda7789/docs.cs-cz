---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 8f28ecc33eea99150509bb4bade047489b4b826b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352304"
---
# <a name="para-visual-basic"></a><span data-ttu-id="4fb5b-101">> \<param (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fb5b-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="4fb5b-102">Určuje, že obsah je formátován jako odstavec.</span><span class="sxs-lookup"><span data-stu-id="4fb5b-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb5b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fb5b-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fb5b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fb5b-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="4fb5b-105">Text odstavce</span><span class="sxs-lookup"><span data-stu-id="4fb5b-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fb5b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fb5b-106">Remarks</span></span>  
 <span data-ttu-id="4fb5b-107">Značka `<para>` je určena pro použití uvnitř značky, jako je například [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [\<vrací >](../../../visual-basic/language-reference/xmldoc/returns.md)a umožňuje přidat do textu strukturu.</span><span class="sxs-lookup"><span data-stu-id="4fb5b-107">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="4fb5b-108">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="4fb5b-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fb5b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fb5b-109">Example</span></span>  
 <span data-ttu-id="4fb5b-110">V tomto příkladu se používá značka `<para>` k rozdělení oddílu poznámky pro metodu `UpdateRecord` na dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="4fb5b-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4fb5b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fb5b-111">See also</span></span>

- [<span data-ttu-id="4fb5b-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="4fb5b-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
