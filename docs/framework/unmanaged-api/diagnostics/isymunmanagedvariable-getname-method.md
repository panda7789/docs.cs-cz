---
title: ISymUnmanagedVariable::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e863640e18ca64de084331327e0fa39468b54b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797537"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="f3559-102">ISymUnmanagedVariable::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="f3559-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="f3559-103">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="f3559-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3559-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3559-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3559-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3559-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f3559-106">[in] Délka vyrovnávací paměti, která `pcchName` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="f3559-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f3559-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f3559-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="f3559-108">[out] Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="f3559-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3559-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f3559-109">Return Value</span></span>  
 <span data-ttu-id="f3559-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f3559-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3559-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3559-111">Requirements</span></span>  
 <span data-ttu-id="f3559-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3559-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3559-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3559-113">See also</span></span>

- [<span data-ttu-id="f3559-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3559-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
