---
title: '&lt;Hodnota&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 92c8c2ac7b95e97b37c907e3837bc90dac384b33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558940"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="17da2-102">&lt;Hodnota&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17da2-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="17da2-103">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17da2-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17da2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17da2-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17da2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17da2-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="17da2-106">Popis pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="17da2-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17da2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17da2-107">Remarks</span></span>  
 <span data-ttu-id="17da2-108">Použití `<value>` značku k popisu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17da2-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="17da2-109">Všimněte si, že při přidání vlastnosti pomocí Průvodce kódem ve vývojovém prostředí sady Visual Studio přidá [ \<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) značky pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="17da2-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="17da2-110">Měli byste pak ručně přidat `<value>` značka, které popisují hodnotu, která představuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="17da2-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="17da2-111">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="17da2-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17da2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="17da2-112">Example</span></span>  
 <span data-ttu-id="17da2-113">V tomto příkladu `<value>` značka, které popisují, jaká hodnota `Counter` vlastnost obsahuje.</span><span class="sxs-lookup"><span data-stu-id="17da2-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="17da2-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17da2-114">See also</span></span>
- [<span data-ttu-id="17da2-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="17da2-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
