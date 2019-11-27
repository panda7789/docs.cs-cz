---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 1cbac2162bd39cdc8af9a55dfd6e2f90bc40b08a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354326"
---
# <a name="code-visual-basic"></a><span data-ttu-id="9659f-101">> kódu \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9659f-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="9659f-102">Označuje, že je text více řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="9659f-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9659f-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9659f-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9659f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9659f-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="9659f-105">Text, který se má označit jako kód</span><span class="sxs-lookup"><span data-stu-id="9659f-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9659f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9659f-106">Remarks</span></span>  
 <span data-ttu-id="9659f-107">Použijte značku `<code>` k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="9659f-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="9659f-108">Použijte [\<> c](../../../visual-basic/language-reference/xmldoc/c.md) k označení toho, že text v rámci popisu by měl být označený jako kód.</span><span class="sxs-lookup"><span data-stu-id="9659f-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="9659f-109">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="9659f-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9659f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9659f-110">Example</span></span>  
 <span data-ttu-id="9659f-111">V tomto příkladu se používá značka \<Code > k zahrnutí ukázkového kódu pro použití pole `ID`.</span><span class="sxs-lookup"><span data-stu-id="9659f-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9659f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9659f-112">See also</span></span>

- [<span data-ttu-id="9659f-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="9659f-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
