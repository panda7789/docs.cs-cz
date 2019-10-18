---
title: <code> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d4e887e3bbbc01e4cef5278f67b8c4afe273bf28
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524036"
---
# <a name="code-visual-basic"></a><span data-ttu-id="e678e-101">\<code > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e678e-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="e678e-102">Označuje, že je text více řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="e678e-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e678e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e678e-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e678e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e678e-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e678e-105">Text, který se má označit jako kód</span><span class="sxs-lookup"><span data-stu-id="e678e-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e678e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e678e-106">Remarks</span></span>  
 <span data-ttu-id="e678e-107">Použijte značku `<code>` k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="e678e-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="e678e-108">Použijte [\<c >](../../../visual-basic/language-reference/xmldoc/c.md) k označení, že text v rámci popisu by měl být označený jako kód.</span><span class="sxs-lookup"><span data-stu-id="e678e-108">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="e678e-109">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="e678e-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e678e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e678e-110">Example</span></span>  
 <span data-ttu-id="e678e-111">V tomto příkladu se používá značka > \<code k zahrnutí vzorového kódu pro použití pole `ID`.</span><span class="sxs-lookup"><span data-stu-id="e678e-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e678e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e678e-112">See also</span></span>

- [<span data-ttu-id="e678e-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="e678e-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
