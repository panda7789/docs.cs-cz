---
title: ISymUnmanagedSourceServerModule::GetSourceServerData – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: f25150d037a2f6fabb700f2c4bf2191e8e402a8e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446217"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="6ced4-102">ISymUnmanagedSourceServerModule::GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="6ced4-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="6ced4-103">Returns the source server data for the module.</span><span class="sxs-lookup"><span data-stu-id="6ced4-103">Returns the source server data for the module.</span></span> <span data-ttu-id="6ced4-104">The caller must free resources by using `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="6ced4-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ced4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ced4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ced4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ced4-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="6ced4-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span><span class="sxs-lookup"><span data-stu-id="6ced4-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="6ced4-108">[out] A pointer to the returned `pDataByteCount` value.</span><span class="sxs-lookup"><span data-stu-id="6ced4-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ced4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ced4-109">Return Value</span></span>  
 <span data-ttu-id="6ced4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="6ced4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ced4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ced4-111">Requirements</span></span>  
 <span data-ttu-id="6ced4-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ced4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ced4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ced4-113">See also</span></span>

- [<span data-ttu-id="6ced4-114">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ced4-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
