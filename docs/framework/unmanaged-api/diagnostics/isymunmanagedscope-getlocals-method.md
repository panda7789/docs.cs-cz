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
ms.openlocfilehash: 0acd31d85504688427cace0222a657885035c537
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615381"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="98620-102">ISymUnmanagedScope::GetLocals – metoda</span><span class="sxs-lookup"><span data-stu-id="98620-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="98620-103">Získá místní proměnné definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="98620-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98620-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98620-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98620-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98620-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="98620-106">pro `ULONG32`Který označuje velikost `locals` pole.</span><span class="sxs-lookup"><span data-stu-id="98620-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="98620-107">mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k uložení místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="98620-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="98620-108">mimo Pole, které přijímá místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="98620-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98620-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98620-109">Return Value</span></span>  
 <span data-ttu-id="98620-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="98620-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98620-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98620-111">Requirements</span></span>  
 <span data-ttu-id="98620-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="98620-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98620-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="98620-113">See also</span></span>

- [<span data-ttu-id="98620-114">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98620-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
