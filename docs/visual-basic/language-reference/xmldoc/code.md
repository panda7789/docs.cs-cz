---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400138"
---
# <a name="code-visual-basic"></a><span data-ttu-id="ed3a3-101">\<code> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed3a3-101">\<code> (Visual Basic)</span></span>
<span data-ttu-id="ed3a3-102">Označuje, že je text více řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-102">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3a3-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed3a3-103">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed3a3-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed3a3-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="ed3a3-105">Text, který se má označit jako kód</span><span class="sxs-lookup"><span data-stu-id="ed3a3-105">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed3a3-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed3a3-106">Remarks</span></span>  
 <span data-ttu-id="ed3a3-107">Použijte `<code>` značku k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-107">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="ed3a3-108">Slouží [\<c>](c.md) k označení, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-108">Use [\<c>](c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="ed3a3-109">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-109">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed3a3-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed3a3-110">Example</span></span>  
 <span data-ttu-id="ed3a3-111">Tento příklad používá \<code> značku k zahrnutí příkladu kódu pro použití `ID` pole.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-111">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ed3a3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed3a3-112">See also</span></span>

- [<span data-ttu-id="ed3a3-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ed3a3-113">XML Comment Tags</span></span>](index.md)
