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
ms.openlocfilehash: ea8052152b08732906c707648f361bba4d83a276
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761556"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="a75ee-102">ISymUnmanagedSourceServerModule::GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="a75ee-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="a75ee-103">Vrací data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="a75ee-103">Returns the source server data for the module.</span></span> <span data-ttu-id="a75ee-104">Volající musí uvolnit prostředky pomocí `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="a75ee-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75ee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a75ee-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75ee-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a75ee-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="a75ee-107">[out] Ukazatel `ULONG32` , která obdrží velikost v bajtech, data ze zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="a75ee-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a75ee-108">[out] Ukazatel na vrácenou `pDataByteCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a75ee-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a75ee-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a75ee-109">Return Value</span></span>  
 <span data-ttu-id="a75ee-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a75ee-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75ee-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a75ee-111">Requirements</span></span>  
 <span data-ttu-id="a75ee-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a75ee-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75ee-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a75ee-113">See also</span></span>

- [<span data-ttu-id="a75ee-114">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a75ee-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
