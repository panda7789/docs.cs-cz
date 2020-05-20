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
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615316"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="b8c4e-102">ISymUnmanagedSourceServerModule::GetSourceServerData – metoda</span><span class="sxs-lookup"><span data-stu-id="b8c4e-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="b8c4e-103">Vrátí data zdrojového serveru pro modul.</span><span class="sxs-lookup"><span data-stu-id="b8c4e-103">Returns the source server data for the module.</span></span> <span data-ttu-id="b8c4e-104">Volající musí uvolnit prostředky pomocí `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="b8c4e-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8c4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8c4e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8c4e-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="b8c4e-107">mimo Ukazatel na `ULONG32` , který obdrží velikost dat zdrojového serveru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b8c4e-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="b8c4e-108">mimo Ukazatel na vrácenou `pDataByteCount` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b8c4e-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8c4e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8c4e-109">Return Value</span></span>  
 <span data-ttu-id="b8c4e-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b8c4e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c4e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8c4e-111">Requirements</span></span>  
 <span data-ttu-id="b8c4e-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b8c4e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c4e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8c4e-113">See also</span></span>

- [<span data-ttu-id="b8c4e-114">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8c4e-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
