---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 2938d485bf6c547c792431b93fc8959c9c36befa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821410"
---
# <a name="value-visual-basic"></a><span data-ttu-id="6d54f-102">\<Hodnota > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d54f-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="6d54f-103">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d54f-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d54f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d54f-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d54f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d54f-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6d54f-106">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d54f-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d54f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d54f-107">Remarks</span></span>  
 <span data-ttu-id="6d54f-108">Použití `<value>` značku k popisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d54f-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="6d54f-109">Všimněte si, že při přidání vlastnosti pomocí Průvodce kódem ve vývojovém prostředí sady Visual Studio přidá [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d54f-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="6d54f-110">Měli byste pak ručně přidat `<value>` značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6d54f-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6d54f-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d54f-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d54f-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d54f-112">Example</span></span>  
 <span data-ttu-id="6d54f-113">V tomto příkladu `<value>` značka, které popisují, jaká hodnota `Counter` vlastnost obsahuje.</span><span class="sxs-lookup"><span data-stu-id="6d54f-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6d54f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d54f-114">See also</span></span>

- [<span data-ttu-id="6d54f-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6d54f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
