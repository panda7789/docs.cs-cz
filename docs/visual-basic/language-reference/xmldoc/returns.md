---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 62f70ae7f40fa3cde9492563b7bd14dfa5940a5f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352247"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="0788e-101">\<vrátí > (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0788e-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="0788e-102">Určuje návratovou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="0788e-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0788e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0788e-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0788e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0788e-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0788e-105">Popis návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0788e-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0788e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0788e-106">Remarks</span></span>  
 <span data-ttu-id="0788e-107">Použijte značku `<returns>` v komentáři pro deklaraci metody k popisu návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0788e-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="0788e-108">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="0788e-108">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0788e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="0788e-109">Example</span></span>  
 <span data-ttu-id="0788e-110">V tomto příkladu se používá značka `<returns>` k vysvětlení, co funkce `DoesRecordExist` vrací.</span><span class="sxs-lookup"><span data-stu-id="0788e-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0788e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0788e-111">See also</span></span>

- [<span data-ttu-id="0788e-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="0788e-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
