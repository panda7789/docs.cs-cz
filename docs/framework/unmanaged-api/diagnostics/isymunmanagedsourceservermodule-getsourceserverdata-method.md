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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc041896615e906ac49eed9a7be139dff217463
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427008"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="7f66d-102">ISymUnmanagedSourceServerModule::GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="7f66d-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="7f66d-103">Vrátí zdroje dat serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="7f66d-103">Returns the source server data for the module.</span></span> <span data-ttu-id="7f66d-104">Volající musí uvolnit prostředky pomocí `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="7f66d-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f66d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f66d-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f66d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f66d-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="7f66d-107">[out] Ukazatel na `ULONG32` velikostí, která přijme v bajtech, zdroj dat serveru.</span><span class="sxs-lookup"><span data-stu-id="7f66d-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="7f66d-108">[out] Ukazatel na vrácený `pDataByteCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7f66d-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f66d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f66d-109">Return Value</span></span>  
 <span data-ttu-id="7f66d-110">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7f66d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f66d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f66d-111">Requirements</span></span>  
 <span data-ttu-id="7f66d-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f66d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f66d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f66d-113">See Also</span></span>  
 [<span data-ttu-id="7f66d-114">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f66d-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
