---
title: '&lt;Param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: cc9ceccef8123d49d6267276e9dcb7be84f78a01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670677"
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="af75d-102">&lt;Param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af75d-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="af75d-103">Definuje parametr název a popis.</span><span class="sxs-lookup"><span data-stu-id="af75d-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af75d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af75d-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af75d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af75d-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="af75d-106">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="af75d-106">The name of a method parameter.</span></span> <span data-ttu-id="af75d-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="af75d-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="af75d-108">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="af75d-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af75d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af75d-109">Remarks</span></span>  
 <span data-ttu-id="af75d-110">`<param>` Značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="af75d-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="af75d-111">Text `<param>` značky se objeví v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="af75d-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="af75d-112">Informace o parametru technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="af75d-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="af75d-113">Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="af75d-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="af75d-114">Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="af75d-114">Object Browser.</span></span> <span data-ttu-id="af75d-115">Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="af75d-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="af75d-116">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="af75d-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af75d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="af75d-117">Example</span></span>  
 <span data-ttu-id="af75d-118">V tomto příkladu `<param>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="af75d-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="af75d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af75d-119">See also</span></span>
- [<span data-ttu-id="af75d-120">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="af75d-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
