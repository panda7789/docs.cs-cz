---
title: '&lt;Param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4cb3de06d574f8b9abb3e3e11641a6ada750b56a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935755"
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="45461-102">&lt;Param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45461-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="45461-103">Definuje parametr název a popis.</span><span class="sxs-lookup"><span data-stu-id="45461-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45461-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45461-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45461-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="45461-106">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="45461-106">The name of a method parameter.</span></span> <span data-ttu-id="45461-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="45461-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="45461-108">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="45461-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45461-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45461-109">Remarks</span></span>  
 <span data-ttu-id="45461-110">`<param>` Značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="45461-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="45461-111">Text `<param>` značky se objeví v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="45461-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="45461-112">Informace o parametru technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="45461-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="45461-113">Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="45461-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="45461-114">Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="45461-114">Object Browser.</span></span> <span data-ttu-id="45461-115">Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="45461-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="45461-116">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="45461-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45461-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="45461-117">Example</span></span>  
 <span data-ttu-id="45461-118">V tomto příkladu `<param>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="45461-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45461-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="45461-119">See Also</span></span>  
 [<span data-ttu-id="45461-120">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="45461-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
