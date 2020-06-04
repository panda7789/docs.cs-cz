---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400018"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="d5374-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5374-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="d5374-102">Určuje oddíl poznámky pro člena.</span><span class="sxs-lookup"><span data-stu-id="d5374-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5374-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5374-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5374-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5374-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="d5374-105">Popis člena</span><span class="sxs-lookup"><span data-stu-id="d5374-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5374-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5374-106">Remarks</span></span>  
 <span data-ttu-id="d5374-107">Pomocí `<remarks>` značky můžete přidat informace o typu a doplnit informace zadané pomocí [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="d5374-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="d5374-108">Tyto informace se zobrazí v Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="d5374-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="d5374-109">Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="d5374-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="d5374-110">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="d5374-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5374-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5374-111">Example</span></span>  
 <span data-ttu-id="d5374-112">Tento příklad používá `<remarks>` značku k vysvětlení, co `UpdateRecord` metoda dělá.</span><span class="sxs-lookup"><span data-stu-id="d5374-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d5374-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5374-113">See also</span></span>

- [<span data-ttu-id="d5374-114">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="d5374-114">XML Comment Tags</span></span>](index.md)
