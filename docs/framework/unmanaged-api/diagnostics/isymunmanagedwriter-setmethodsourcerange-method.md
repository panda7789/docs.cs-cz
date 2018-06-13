---
title: ISymUnmanagedWriter::SetMethodSourceRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d057201c7d7bec3070027bb1d9de62735d583cf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428999"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="5a675-102">ISymUnmanagedWriter::SetMethodSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="5a675-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="5a675-103">Určuje hodnotu true počáteční a koncová metody v rámci zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="5a675-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="5a675-104">Tuto metodu použijte k určení rozsahu metoda nezávisle na pořadí body, které existují v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="5a675-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a675-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a675-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a675-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a675-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="5a675-107">[v] Ukazatel na dokument obsahující počáteční pozici.</span><span class="sxs-lookup"><span data-stu-id="5a675-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="5a675-108">[v] Počáteční řádek číslo.</span><span class="sxs-lookup"><span data-stu-id="5a675-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="5a675-109">[v] Počáteční sloupec.</span><span class="sxs-lookup"><span data-stu-id="5a675-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="5a675-110">[v] Ukazatel na dokument obsahující koncovou pozici.</span><span class="sxs-lookup"><span data-stu-id="5a675-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="5a675-111">[v] Koncová číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="5a675-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="5a675-112">[v] Koncová číslo sloupce.</span><span class="sxs-lookup"><span data-stu-id="5a675-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a675-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a675-113">Return Value</span></span>  
 <span data-ttu-id="5a675-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5a675-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a675-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a675-115">Requirements</span></span>  
 <span data-ttu-id="5a675-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a675-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a675-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a675-117">See Also</span></span>  
 [<span data-ttu-id="5a675-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a675-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
