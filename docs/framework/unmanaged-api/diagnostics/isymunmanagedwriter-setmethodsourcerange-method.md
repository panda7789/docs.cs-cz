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
ms.openlocfilehash: 40d05ee60d0183337e67b1f36722dff29ae9beaf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663541"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="1ad5d-102">ISymUnmanagedWriter::SetMethodSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1ad5d-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="1ad5d-103">Určuje hodnotu true začátku a konce metody v rámci zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="1ad5d-104">Tuto metodu použijte k určení rozsahu metody bez ohledu na jejich body sekvence, které existují v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad5d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ad5d-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ad5d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ad5d-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="1ad5d-107">[in] Ukazatel na dokument obsahující počáteční pozice.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="1ad5d-108">[in] Počáteční řádek číslo.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="1ad5d-109">[in] Počáteční sloupec.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="1ad5d-110">[in] Ukazatel na dokument obsahující koncovou pozici.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="1ad5d-111">[in] Koncové číslo řádku.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="1ad5d-112">[in] Koncové číslo sloupce.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ad5d-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ad5d-113">Return Value</span></span>  
 <span data-ttu-id="1ad5d-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1ad5d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ad5d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ad5d-115">Requirements</span></span>  
 <span data-ttu-id="1ad5d-116">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1ad5d-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad5d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ad5d-117">See also</span></span>
- [<span data-ttu-id="1ad5d-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ad5d-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
