---
title: ISymUnmanagedENCUpdate::GetLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: b5fc8b6807a4c8eb700ab3fa181a216e48a732ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449030"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="430e9-102">ISymUnmanagedENCUpdate::GetLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="430e9-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="430e9-103">Získá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="430e9-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="430e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="430e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="430e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="430e9-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="430e9-106">pro Token metadat metody</span><span class="sxs-lookup"><span data-stu-id="430e9-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="430e9-107">pro `ULONG`, která určuje velikost `rgLocals` parametru.</span><span class="sxs-lookup"><span data-stu-id="430e9-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="430e9-108">mimo Vrácené pole instancí [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="430e9-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="430e9-109">mimo Ukazatel na `ULONG`, který přijímá velikost `rgLocals` vyrovnávací paměti, která je požadována pro uložení místních hodnot.</span><span class="sxs-lookup"><span data-stu-id="430e9-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="430e9-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="430e9-110">Return Value</span></span>  
 <span data-ttu-id="430e9-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="430e9-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430e9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="430e9-112">Requirements</span></span>  
 <span data-ttu-id="430e9-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="430e9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430e9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="430e9-114">See also</span></span>

- [<span data-ttu-id="430e9-115">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="430e9-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
