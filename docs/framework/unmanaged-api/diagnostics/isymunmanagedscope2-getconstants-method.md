---
title: ISymUnmanagedScope2::GetConstants – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176614"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="25ac4-102">ISymUnmanagedScope2::GetConstants – metoda</span><span class="sxs-lookup"><span data-stu-id="25ac4-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="25ac4-103">Získá místní konstanty definované v rámci tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="25ac4-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25ac4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ac4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25ac4-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="25ac4-106">[v] Délka vyrovnávací paměti, `pcConstants` na kterou parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="25ac4-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="25ac4-107">[out] Ukazatel na `ULONG32` který obdrží velikost, ve znacích vyrovnávací paměti potřebné k obsahovat konstanty.</span><span class="sxs-lookup"><span data-stu-id="25ac4-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="25ac4-108">[out] Vyrovnávací paměť, která ukládá konstanty.</span><span class="sxs-lookup"><span data-stu-id="25ac4-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25ac4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25ac4-109">Return Value</span></span>  
 <span data-ttu-id="25ac4-110">S_OK pokud je metoda úspěšná; v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="25ac4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ac4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25ac4-111">Requirements</span></span>  
 <span data-ttu-id="25ac4-112">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25ac4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ac4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="25ac4-113">See also</span></span>

- [<span data-ttu-id="25ac4-114">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25ac4-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
