---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: f80d9f3024107ace2102fb9ec9e8657d3219aafa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502238"
---
# <a name="param-visual-basic"></a><span data-ttu-id="c9d8f-102">\<Param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9d8f-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="c9d8f-103">Definuje parametr název a popis.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d8f-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9d8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9d8f-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c9d8f-106">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-106">The name of a method parameter.</span></span> <span data-ttu-id="c9d8f-107">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="c9d8f-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c9d8f-108">Popis pro parametr.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9d8f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9d8f-109">Remarks</span></span>  
 <span data-ttu-id="c9d8f-110">`<param>` Značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="c9d8f-111">Text `<param>` značky se objeví v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="c9d8f-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="c9d8f-112">Informace o parametru technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="c9d8f-113">Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="c9d8f-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="c9d8f-114">Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-114">Object Browser.</span></span> <span data-ttu-id="c9d8f-115">Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="c9d8f-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="c9d8f-116">Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9d8f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9d8f-117">Example</span></span>  
 <span data-ttu-id="c9d8f-118">V tomto příkladu `<param>` značka, které popisují `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="c9d8f-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c9d8f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9d8f-119">See also</span></span>
- [<span data-ttu-id="c9d8f-120">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="c9d8f-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
