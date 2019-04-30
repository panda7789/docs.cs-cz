---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a75ca89a3537ce8ee72e8ba24401800eacff20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939734"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="0a58e-102">ISymUnmanagedENCUpdate::GetLocalVariableCount – metoda</span><span class="sxs-lookup"><span data-stu-id="0a58e-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="0a58e-103">Získá počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="0a58e-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a58e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a58e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a58e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a58e-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="0a58e-106">[in] Token metadat z metod.</span><span class="sxs-lookup"><span data-stu-id="0a58e-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="0a58e-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat počet místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="0a58e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a58e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a58e-108">Return Value</span></span>  
 <span data-ttu-id="0a58e-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0a58e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a58e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a58e-110">Requirements</span></span>  
 <span data-ttu-id="0a58e-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a58e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a58e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a58e-112">See also</span></span>

- [<span data-ttu-id="0a58e-113">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a58e-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
