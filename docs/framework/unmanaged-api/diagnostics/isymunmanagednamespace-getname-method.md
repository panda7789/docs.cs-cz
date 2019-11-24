---
title: ISymUnmanagedNamespace::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 43f32ac85bebc12d0a9253205aae3f1de0dc9e5b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433973"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="12f67-102">ISymUnmanagedNamespace::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="12f67-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="12f67-103">Gets the name of this namespace.</span><span class="sxs-lookup"><span data-stu-id="12f67-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12f67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12f67-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="12f67-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="12f67-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="12f67-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span><span class="sxs-lookup"><span data-stu-id="12f67-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="12f67-108">[out] A pointer to a buffer that contains the namespace name.</span><span class="sxs-lookup"><span data-stu-id="12f67-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12f67-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="12f67-109">Return Value</span></span>  
 <span data-ttu-id="12f67-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="12f67-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f67-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f67-111">Requirements</span></span>  
 <span data-ttu-id="12f67-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12f67-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f67-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f67-113">See also</span></span>

- [<span data-ttu-id="12f67-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f67-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
