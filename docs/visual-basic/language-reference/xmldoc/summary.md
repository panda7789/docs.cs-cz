---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3f40177b717452f316672c29c6455faf33e01b4d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282708"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="f6178-102">\<Souhrn > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6178-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="f6178-103">Určuje souhrn člena.</span><span class="sxs-lookup"><span data-stu-id="f6178-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6178-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6178-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6178-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6178-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f6178-106">Přehled objektu.</span><span class="sxs-lookup"><span data-stu-id="f6178-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6178-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6178-107">Remarks</span></span>  
 <span data-ttu-id="f6178-108">Použití `<summary>` značka, které popisují typ nebo člen typu.</span><span class="sxs-lookup"><span data-stu-id="f6178-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="f6178-109">Použití [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) přidat doplňující informace pro popis typu.</span><span class="sxs-lookup"><span data-stu-id="f6178-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="f6178-110">Text `<summary>` značka je jediný zdroj informací o typu v IntelliSense a také se zobrazí v prohlížeči objektů.</span><span class="sxs-lookup"><span data-stu-id="f6178-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="f6178-111">Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="f6178-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="f6178-112">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="f6178-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6178-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6178-113">Example</span></span>  
 <span data-ttu-id="f6178-114">V tomto příkladu `<summary>` značka, které popisují `ResetCounter` metoda a `Counter` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f6178-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f6178-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6178-115">See also</span></span>
- [<span data-ttu-id="f6178-116">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="f6178-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
