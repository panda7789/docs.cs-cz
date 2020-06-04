---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: edbc374332bdcd67b385ac3d061045664e942460
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84399992"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="ad1a6-101">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad1a6-101">\<returns> (Visual Basic)</span></span>
<span data-ttu-id="ad1a6-102">Určuje návratovou hodnotu vlastnosti nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-102">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1a6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1a6-103">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad1a6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad1a6-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="ad1a6-105">Popis návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-105">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1a6-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad1a6-106">Remarks</span></span>  
 <span data-ttu-id="ad1a6-107">Použijte `<returns>` značku v komentáři pro deklaraci metody k popisu návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-107">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="ad1a6-108">Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad1a6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad1a6-109">Example</span></span>  
 <span data-ttu-id="ad1a6-110">Tento příklad používá `<returns>` značku k vysvětlení, co `DoesRecordExist` funkce vrací.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-110">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ad1a6-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad1a6-111">See also</span></span>

- [<span data-ttu-id="ad1a6-112">Značky pro komentáře XML</span><span class="sxs-lookup"><span data-stu-id="ad1a6-112">XML Comment Tags</span></span>](index.md)
