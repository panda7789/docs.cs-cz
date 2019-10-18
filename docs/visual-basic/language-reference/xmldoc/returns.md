---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524679"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="33af2-102">\<returns > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33af2-102">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="33af2-103">Určuje návratovou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="33af2-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33af2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33af2-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="33af2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33af2-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="33af2-106">Popis návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33af2-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33af2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33af2-107">Remarks</span></span>  
 <span data-ttu-id="33af2-108">Použijte značku `<returns>` v komentáři pro deklaraci metody k popisu návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="33af2-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="33af2-109">Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="33af2-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33af2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="33af2-110">Example</span></span>  
 <span data-ttu-id="33af2-111">V tomto příkladu se používá značka `<returns>` k vysvětlení, co funkce `DoesRecordExist` vrací.</span><span class="sxs-lookup"><span data-stu-id="33af2-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="33af2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33af2-112">See also</span></span>

- [<span data-ttu-id="33af2-113">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="33af2-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
