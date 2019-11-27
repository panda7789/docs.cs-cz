---
title: ISymUnmanagedVariable::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
ms.openlocfilehash: 2939d9cf3991a9e0b8f93bb301925b1092eca50e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446043"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="5f0e7-102">ISymUnmanagedVariable::GetSignature – metoda</span><span class="sxs-lookup"><span data-stu-id="5f0e7-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="5f0e7-103">Načte podpis této proměnné.</span><span class="sxs-lookup"><span data-stu-id="5f0e7-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f0e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f0e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f0e7-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="5f0e7-106">pro Délka vyrovnávací paměti, na kterou ukazuje parametr `sig`.</span><span class="sxs-lookup"><span data-stu-id="5f0e7-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="5f0e7-107">mimo Ukazatel na `ULONG32`, který obdrží velikost vyrovnávací paměti, která je požadována k podpisu.</span><span class="sxs-lookup"><span data-stu-id="5f0e7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="5f0e7-108">mimo Vyrovnávací paměť, která ukládá podpis.</span><span class="sxs-lookup"><span data-stu-id="5f0e7-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f0e7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5f0e7-109">Return Value</span></span>  
 <span data-ttu-id="5f0e7-110">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5f0e7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f0e7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f0e7-111">Requirements</span></span>  
 <span data-ttu-id="5f0e7-112">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5f0e7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0e7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f0e7-113">See also</span></span>

- [<span data-ttu-id="5f0e7-114">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f0e7-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
