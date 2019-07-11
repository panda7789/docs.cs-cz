---
title: ISymUnmanagedNamespace::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4323423d3958fa1ca652c55f8f75749bb6e1ee79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759383"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="7216a-102">ISymUnmanagedNamespace::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="7216a-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="7216a-103">Získá název tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7216a-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7216a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7216a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7216a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7216a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7216a-106">[in] A `ULONG32` , který označuje velikost `szName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7216a-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7216a-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat obor názvů, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="7216a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="7216a-108">[out] Ukazatel do vyrovnávací paměti, který obsahuje název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7216a-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7216a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7216a-109">Return Value</span></span>  
 <span data-ttu-id="7216a-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7216a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7216a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7216a-111">Requirements</span></span>  
 <span data-ttu-id="7216a-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7216a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7216a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7216a-113">See also</span></span>

- [<span data-ttu-id="7216a-114">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7216a-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
