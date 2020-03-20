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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176575"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="969b6-102">ISymUnmanagedSourceServerModule::GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="969b6-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="969b6-103">Vrátí data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="969b6-103">Returns the source server data for the module.</span></span> <span data-ttu-id="969b6-104">Volající musí uvolnit prostředky `CoTaskMemFree`pomocí .</span><span class="sxs-lookup"><span data-stu-id="969b6-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="969b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="969b6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="969b6-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="969b6-107">[out] Ukazatel na `ULONG32` který přijímá velikost dat zdrojového serveru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="969b6-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="969b6-108">[out] Ukazatel na vrácenou `pDataByteCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="969b6-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="969b6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="969b6-109">Return Value</span></span>  
 <span data-ttu-id="969b6-110">S_OK pokud je metoda úspěšná; v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="969b6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="969b6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="969b6-111">Requirements</span></span>  
 <span data-ttu-id="969b6-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="969b6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969b6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="969b6-113">See also</span></span>

- [<span data-ttu-id="969b6-114">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="969b6-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
