---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 74002ce9c76eebaa3ea5860b09cd3e7c9a884f8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448651"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="315bf-102">ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="315bf-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="315bf-103">Gets the file name for the line associated with an offset.</span><span class="sxs-lookup"><span data-stu-id="315bf-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="315bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="315bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="315bf-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="315bf-106">[in] A `ULONG32` that contains the offset.</span><span class="sxs-lookup"><span data-stu-id="315bf-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="315bf-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="315bf-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="315bf-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span><span class="sxs-lookup"><span data-stu-id="315bf-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="315bf-109">[out] The buffer that contains the file names.</span><span class="sxs-lookup"><span data-stu-id="315bf-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="315bf-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="315bf-110">Return Value</span></span>  
 <span data-ttu-id="315bf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="315bf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315bf-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="315bf-112">Requirements</span></span>  
 <span data-ttu-id="315bf-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="315bf-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315bf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="315bf-114">See also</span></span>

- [<span data-ttu-id="315bf-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="315bf-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
