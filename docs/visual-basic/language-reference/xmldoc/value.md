---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352175"
---
# <a name="value-visual-basic"></a><span data-ttu-id="25f1b-101">\<hodnota > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25f1b-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="25f1b-102">Určuje popis vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25f1b-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f1b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f1b-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="25f1b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="25f1b-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="25f1b-105">Popis vlastnosti</span><span class="sxs-lookup"><span data-stu-id="25f1b-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25f1b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25f1b-106">Remarks</span></span>  
 <span data-ttu-id="25f1b-107">K popisu vlastnosti použijte značku `<value>`.</span><span class="sxs-lookup"><span data-stu-id="25f1b-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="25f1b-108">Všimněte si, že při přidání vlastnosti pomocí průvodce kódem ve vývojovém prostředí sady Visual Studio bude přidána značka [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) pro novou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="25f1b-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="25f1b-109">Měli byste pak ručně přidat značku `<value>` k popisu hodnoty, kterou vlastnost představuje.</span><span class="sxs-lookup"><span data-stu-id="25f1b-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="25f1b-110">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="25f1b-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25f1b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="25f1b-111">Example</span></span>  
 <span data-ttu-id="25f1b-112">V tomto příkladu se používá značka `<value>` k popisu hodnoty, které vlastnost `Counter` obsahuje.</span><span class="sxs-lookup"><span data-stu-id="25f1b-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="25f1b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25f1b-113">See also</span></span>

- [<span data-ttu-id="25f1b-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="25f1b-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
