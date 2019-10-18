---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524603"
---
# <a name="value-visual-basic"></a><span data-ttu-id="3e083-102">\<value > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e083-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="3e083-103">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3e083-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e083-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e083-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e083-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e083-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="3e083-106">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3e083-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e083-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e083-107">Remarks</span></span>  
 <span data-ttu-id="3e083-108">K popisu vlastnosti použijte značku `<value>`.</span><span class="sxs-lookup"><span data-stu-id="3e083-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="3e083-109">Všimněte si, že při přidání vlastnosti pomocí průvodce kódem ve vývojovém prostředí sady Visual Studio bude přidána značka [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3e083-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="3e083-110">Měli byste pak ručně přidat značku `<value>` k popisu hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="3e083-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3e083-111">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="3e083-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e083-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e083-112">Example</span></span>  
 <span data-ttu-id="3e083-113">V tomto příkladu se používá značka `<value>` k popisu hodnoty, které vlastnost `Counter` obsahuje.</span><span class="sxs-lookup"><span data-stu-id="3e083-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e083-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e083-114">See also</span></span>

- [<span data-ttu-id="3e083-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="3e083-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
