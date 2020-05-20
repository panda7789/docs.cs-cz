---
title: ISymUnmanagedMethod::GetParameters – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: 031e9d9434bc655ba8947a2bb6aba56a150e9002
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614458"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="e07d8-102">ISymUnmanagedMethod::GetParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="e07d8-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="e07d8-103">Získá parametry pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="e07d8-103">Gets the parameters for this method.</span></span> <span data-ttu-id="e07d8-104">Parametry jsou vráceny v pořadí, ve kterém jsou definovány v rámci signatury metody.</span><span class="sxs-lookup"><span data-stu-id="e07d8-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07d8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e07d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07d8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e07d8-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="e07d8-107">pro Velikost `params` pole.</span><span class="sxs-lookup"><span data-stu-id="e07d8-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="e07d8-108">pro Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je požadována k uložení parametrů.</span><span class="sxs-lookup"><span data-stu-id="e07d8-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="e07d8-109">mimo Ukazatel na vyrovnávací paměť, která přijímá parametry.</span><span class="sxs-lookup"><span data-stu-id="e07d8-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e07d8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e07d8-110">Return Value</span></span>  
 <span data-ttu-id="e07d8-111">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="e07d8-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07d8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e07d8-112">Requirements</span></span>  
 <span data-ttu-id="e07d8-113">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e07d8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07d8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e07d8-114">See also</span></span>

- [<span data-ttu-id="e07d8-115">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e07d8-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
