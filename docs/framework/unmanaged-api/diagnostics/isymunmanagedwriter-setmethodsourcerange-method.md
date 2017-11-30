---
title: "ISymUnmanagedWriter::SetMethodSourceRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ed0a73b4862702895e737f2df639b8da7f7679
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="a318a-102">ISymUnmanagedWriter::SetMethodSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="a318a-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="a318a-103">Určuje hodnotu true počáteční a koncová metody v rámci zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="a318a-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="a318a-104">Tuto metodu použijte k určení rozsahu metoda nezávisle na pořadí body, které existují v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="a318a-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a318a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a318a-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a318a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a318a-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="a318a-107">[v] Ukazatel na dokument obsahující počáteční pozici.</span><span class="sxs-lookup"><span data-stu-id="a318a-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="a318a-108">[v] Počáteční řádek číslo.</span><span class="sxs-lookup"><span data-stu-id="a318a-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="a318a-109">[v] Počáteční sloupec.</span><span class="sxs-lookup"><span data-stu-id="a318a-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="a318a-110">[v] Ukazatel na dokument obsahující koncovou pozici.</span><span class="sxs-lookup"><span data-stu-id="a318a-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="a318a-111">[v] Koncová číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="a318a-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="a318a-112">[v] Koncová číslo sloupce.</span><span class="sxs-lookup"><span data-stu-id="a318a-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a318a-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a318a-113">Return Value</span></span>  
 <span data-ttu-id="a318a-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a318a-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a318a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a318a-115">Requirements</span></span>  
 <span data-ttu-id="a318a-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a318a-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a318a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a318a-117">See Also</span></span>  
 [<span data-ttu-id="a318a-118">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="a318a-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
