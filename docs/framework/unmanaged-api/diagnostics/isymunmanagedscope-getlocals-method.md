---
title: ISymUnmanagedScope::GetLocals – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: bf932b63973f93c56883f099ddaadd9d1519f337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446326"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="4e95e-102">ISymUnmanagedScope::GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="4e95e-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="4e95e-103">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="4e95e-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e95e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e95e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e95e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e95e-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="4e95e-106">pro `ULONG32`, která určuje velikost `locals` pole.</span><span class="sxs-lookup"><span data-stu-id="4e95e-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="4e95e-107">mimo Ukazatel na `ULONG32`, který přijímá velikost vyrovnávací paměti vyžadované k uložení místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="4e95e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="4e95e-108">mimo Pole, které přijímá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="4e95e-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e95e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4e95e-109">Return Value</span></span>  
 <span data-ttu-id="4e95e-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="4e95e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e95e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e95e-111">Requirements</span></span>  
 <span data-ttu-id="4e95e-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4e95e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e95e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e95e-113">See also</span></span>

- [<span data-ttu-id="4e95e-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e95e-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
