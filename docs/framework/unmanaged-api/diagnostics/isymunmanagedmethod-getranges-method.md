---
title: ISymUnmanagedMethod::GetRanges – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: 1f1bd9c33f24847eae4ff7d26c5b996cd34afb72
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448936"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="aa926-102">ISymUnmanagedMethod::GetRanges – metoda</span><span class="sxs-lookup"><span data-stu-id="aa926-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="aa926-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span><span class="sxs-lookup"><span data-stu-id="aa926-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="aa926-104">The array is an array of integers and has the format [start, end, start, end].</span><span class="sxs-lookup"><span data-stu-id="aa926-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="aa926-105">The number of range pairs is the length of the array divided by 2.</span><span class="sxs-lookup"><span data-stu-id="aa926-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa926-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa926-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa926-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa926-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="aa926-108">[in] The document for which the offset is requested.</span><span class="sxs-lookup"><span data-stu-id="aa926-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="aa926-109">[in] The document line corresponding to the ranges.</span><span class="sxs-lookup"><span data-stu-id="aa926-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="aa926-110">[in] The document column corresponding to the ranges.</span><span class="sxs-lookup"><span data-stu-id="aa926-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="aa926-111">[in] The size of the `ranges` array.</span><span class="sxs-lookup"><span data-stu-id="aa926-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="aa926-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span><span class="sxs-lookup"><span data-stu-id="aa926-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="aa926-113">[out] A pointer to the buffer that receives the ranges.</span><span class="sxs-lookup"><span data-stu-id="aa926-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa926-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa926-114">Return Value</span></span>  
 <span data-ttu-id="aa926-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="aa926-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa926-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa926-116">Requirements</span></span>  
 <span data-ttu-id="aa926-117">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aa926-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa926-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa926-118">See also</span></span>

- [<span data-ttu-id="aa926-119">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa926-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
