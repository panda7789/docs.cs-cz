---
title: ISymUnmanagedBinder3::GetReaderFromCallback – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: a0cccc0adfc666cc8e373bc1f89c8f6f97068fde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449311"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="1c274-102">ISymUnmanagedBinder3::GetReaderFromCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="1c274-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="1c274-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span><span class="sxs-lookup"><span data-stu-id="1c274-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c274-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c274-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c274-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c274-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1c274-106">[in] A pointer to the metadata import interface.</span><span class="sxs-lookup"><span data-stu-id="1c274-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1c274-107">[in] A pointer to the file name.</span><span class="sxs-lookup"><span data-stu-id="1c274-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1c274-108">[in] A pointer to the search path.</span><span class="sxs-lookup"><span data-stu-id="1c274-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="1c274-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span><span class="sxs-lookup"><span data-stu-id="1c274-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="1c274-110">[in] A pointer to the callback function.</span><span class="sxs-lookup"><span data-stu-id="1c274-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1c274-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1c274-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c274-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1c274-112">Return Value</span></span>  
 <span data-ttu-id="1c274-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="1c274-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c274-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c274-114">Requirements</span></span>  
 <span data-ttu-id="1c274-115">**Header:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="1c274-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c274-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c274-116">See also</span></span>

- [<span data-ttu-id="1c274-117">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c274-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
