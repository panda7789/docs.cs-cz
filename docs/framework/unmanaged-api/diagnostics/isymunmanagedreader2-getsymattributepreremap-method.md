---
title: ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 4009f8988c90ed090c0cc3d86164af347055722f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446417"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="e73c5-102">ISymUnmanagedReader2::GetSymAttributePreRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="e73c5-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="e73c5-103">Gets a custom attribute based upon its name.</span><span class="sxs-lookup"><span data-stu-id="e73c5-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="e73c5-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span><span class="sxs-lookup"><span data-stu-id="e73c5-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e73c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e73c5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e73c5-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="e73c5-107">[in] The metadata token of the parent.</span><span class="sxs-lookup"><span data-stu-id="e73c5-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="e73c5-108">[in] A pointer to a `WCHAR` that contains the name.</span><span class="sxs-lookup"><span data-stu-id="e73c5-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="e73c5-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span><span class="sxs-lookup"><span data-stu-id="e73c5-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="e73c5-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span><span class="sxs-lookup"><span data-stu-id="e73c5-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e73c5-111">[out] A pointer to the buffer that receives the attribute bytes.</span><span class="sxs-lookup"><span data-stu-id="e73c5-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e73c5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e73c5-112">Return Value</span></span>  
 <span data-ttu-id="e73c5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="e73c5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e73c5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e73c5-114">Requirements</span></span>  
 <span data-ttu-id="e73c5-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e73c5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73c5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e73c5-116">See also</span></span>

- [<span data-ttu-id="e73c5-117">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e73c5-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
