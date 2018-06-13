---
title: '&lt;Hodnota&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602455"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="6523b-102">&lt;Hodnota&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6523b-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="6523b-103">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6523b-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6523b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6523b-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6523b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6523b-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6523b-106">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6523b-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6523b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6523b-107">Remarks</span></span>  
 <span data-ttu-id="6523b-108">Použití `<value>` značka, které popisují vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6523b-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="6523b-109">Všimněte si, že při přidání vlastnosti pomocí Průvodce kódu ve vývojovém prostředí sady Visual Studio, přidá [ \<souhrnné >](../../../visual-basic/language-reference/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6523b-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="6523b-110">Měli byste pak přidat ručně `<value>` značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6523b-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6523b-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="6523b-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6523b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6523b-112">Example</span></span>  
 <span data-ttu-id="6523b-113">Tento příklad používá `<value>` značka, které popisují, jaké hodnoty `Counter` vlastnost blokování.</span><span class="sxs-lookup"><span data-stu-id="6523b-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6523b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6523b-114">See Also</span></span>  
 [<span data-ttu-id="6523b-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="6523b-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
