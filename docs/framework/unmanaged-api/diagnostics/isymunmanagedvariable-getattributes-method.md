---
title: ISymUnmanagedVariable::GetAttributes – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d418a1088f9ee23a088ab4c8246810d2c9bee4fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574336"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="9db88-102">ISymUnmanagedVariable::GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="9db88-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="9db88-103">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="9db88-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9db88-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9db88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9db88-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9db88-106">[out] Ukazatel `ULONG32` , která obdrží atributy.</span><span class="sxs-lookup"><span data-stu-id="9db88-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="9db88-107">Jedna z hodnot fronty definovaných v bude vrácenou hodnotou [corsymvarflag –](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="9db88-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db88-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9db88-108">Return Value</span></span>  
 <span data-ttu-id="9db88-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="9db88-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db88-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9db88-110">Requirements</span></span>  
 <span data-ttu-id="9db88-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9db88-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db88-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9db88-112">See also</span></span>
- [<span data-ttu-id="9db88-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9db88-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
