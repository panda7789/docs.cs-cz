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
ms.openlocfilehash: 4ba3f31ae6d6b67d7beaa2f709bf6174b721136d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609518"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="469a7-102">ISymUnmanagedWriter::SetMethodSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="469a7-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="469a7-103">Určuje skutečný začátek a konec metody ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="469a7-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="469a7-104">Tuto metodu použijte, chcete-li určit rozsah metody nezávisle na sekvenčních bodech, které existují v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="469a7-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="469a7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="469a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="469a7-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="469a7-107">pro Ukazatel na dokument obsahující počáteční pozici.</span><span class="sxs-lookup"><span data-stu-id="469a7-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="469a7-108">pro Číslo počátečního řádku</span><span class="sxs-lookup"><span data-stu-id="469a7-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="469a7-109">pro Počáteční sloupec</span><span class="sxs-lookup"><span data-stu-id="469a7-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="469a7-110">pro Ukazatel na dokument, který obsahuje koncovou pozici.</span><span class="sxs-lookup"><span data-stu-id="469a7-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="469a7-111">pro Koncové číslo řádku</span><span class="sxs-lookup"><span data-stu-id="469a7-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="469a7-112">pro Číslo koncového sloupce</span><span class="sxs-lookup"><span data-stu-id="469a7-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="469a7-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="469a7-113">Return Value</span></span>  
 <span data-ttu-id="469a7-114">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="469a7-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="469a7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="469a7-115">Requirements</span></span>  
 <span data-ttu-id="469a7-116">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="469a7-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469a7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="469a7-117">See also</span></span>

- [<span data-ttu-id="469a7-118">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="469a7-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
