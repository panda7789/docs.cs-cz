---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411496"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="612cf-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="612cf-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="612cf-102">Určuje souhrn člena.</span><span class="sxs-lookup"><span data-stu-id="612cf-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612cf-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="612cf-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="612cf-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="612cf-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="612cf-105">Souhrn objektu.</span><span class="sxs-lookup"><span data-stu-id="612cf-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="612cf-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="612cf-106">Remarks</span></span>  
 <span data-ttu-id="612cf-107">Použijte `<summary>` značku k popisu typu nebo člena typu.</span><span class="sxs-lookup"><span data-stu-id="612cf-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="612cf-108">Slouží [\<remarks>](remarks.md) k přidání doplňujících informací k popisu typu.</span><span class="sxs-lookup"><span data-stu-id="612cf-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="612cf-109">Text `<summary>` značky je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="612cf-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="612cf-110">Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="612cf-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="612cf-111">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="612cf-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="612cf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="612cf-112">Example</span></span>  
 <span data-ttu-id="612cf-113">Tento příklad používá `<summary>` značku k popisu `ResetCounter` metody a `Counter` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="612cf-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="612cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="612cf-114">See also</span></span>

- [<span data-ttu-id="612cf-115">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="612cf-115">XML Comment Tags</span></span>](index.md)
