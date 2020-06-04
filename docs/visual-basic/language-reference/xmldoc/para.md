---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400070"
---
# <a name="para-visual-basic"></a><span data-ttu-id="b4e68-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e68-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="b4e68-102">Určuje, že obsah je formátován jako odstavec.</span><span class="sxs-lookup"><span data-stu-id="b4e68-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e68-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4e68-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4e68-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4e68-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="b4e68-105">Text odstavce</span><span class="sxs-lookup"><span data-stu-id="b4e68-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4e68-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4e68-106">Remarks</span></span>  
 <span data-ttu-id="b4e68-107">`<para>`Značka je určena pro použití uvnitř značky, jako například [\<summary>](summary.md) , [\<remarks>](remarks.md) nebo [\<returns>](returns.md) , a umožňuje přidat do textu strukturu.</span><span class="sxs-lookup"><span data-stu-id="b4e68-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="b4e68-108">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="b4e68-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4e68-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4e68-109">Example</span></span>  
 <span data-ttu-id="b4e68-110">Tento příklad používá `<para>` značku k rozdělení oddílu poznámky pro `UpdateRecord` metodu do dvou odstavců.</span><span class="sxs-lookup"><span data-stu-id="b4e68-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b4e68-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4e68-111">See also</span></span>

- [<span data-ttu-id="b4e68-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="b4e68-112">XML Comment Tags</span></span>](index.md)
