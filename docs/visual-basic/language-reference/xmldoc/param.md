---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524728"
---
# <a name="param-visual-basic"></a><span data-ttu-id="40b87-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40b87-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="40b87-103">Definuje název a popis parametru.</span><span class="sxs-lookup"><span data-stu-id="40b87-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40b87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40b87-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="40b87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40b87-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="40b87-106">Název parametru metody.</span><span class="sxs-lookup"><span data-stu-id="40b87-106">The name of a method parameter.</span></span> <span data-ttu-id="40b87-107">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="40b87-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="40b87-108">Popis parametru</span><span class="sxs-lookup"><span data-stu-id="40b87-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40b87-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40b87-109">Remarks</span></span>  
 <span data-ttu-id="40b87-110">Značka `<param>` by měla být použita v komentáři pro deklaraci metody pro popis jednoho z parametrů pro metodu.</span><span class="sxs-lookup"><span data-stu-id="40b87-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="40b87-111">Text značky `<param>` se zobrazí v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="40b87-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="40b87-112">Informace o parametrech technologie IntelliSense</span><span class="sxs-lookup"><span data-stu-id="40b87-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="40b87-113">Další informace najdete v tématu [použití technologie IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="40b87-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="40b87-114">Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="40b87-114">Object Browser.</span></span> <span data-ttu-id="40b87-115">Další informace naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="40b87-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="40b87-116">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="40b87-116">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40b87-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="40b87-117">Example</span></span>  
 <span data-ttu-id="40b87-118">V tomto příkladu se používá značka `<param>` k popisu `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="40b87-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="40b87-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40b87-119">See also</span></span>

- [<span data-ttu-id="40b87-120">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="40b87-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
