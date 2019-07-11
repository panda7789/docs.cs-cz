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
ms.openlocfilehash: 8298e7240052bdd859dbe414281d8e78984342e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778252"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="9ff51-102">ISymUnmanagedVariable::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="9ff51-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="9ff51-103">Získá název této proměnné.</span><span class="sxs-lookup"><span data-stu-id="9ff51-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ff51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ff51-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9ff51-106">[in] Délka vyrovnávací paměti, která `pcchName` parametr odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="9ff51-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9ff51-107">[out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9ff51-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9ff51-108">[out] Vyrovnávací paměť, která ukládá název.</span><span class="sxs-lookup"><span data-stu-id="9ff51-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ff51-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ff51-109">Return Value</span></span>  
 <span data-ttu-id="9ff51-110">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9ff51-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ff51-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ff51-111">Requirements</span></span>  
 <span data-ttu-id="9ff51-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9ff51-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff51-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ff51-113">See also</span></span>

- [<span data-ttu-id="9ff51-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ff51-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
