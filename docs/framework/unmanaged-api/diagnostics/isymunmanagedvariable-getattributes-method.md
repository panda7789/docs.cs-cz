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
ms.openlocfilehash: f7e71315b5ff99a550ae4a59f3b0d444093dac01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778273"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="0a7d9-102">ISymUnmanagedVariable::GetAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="0a7d9-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="0a7d9-103">Získá příznaky atributu pro tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0a7d9-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a7d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a7d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a7d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a7d9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0a7d9-106">[out] Ukazatel `ULONG32` , která obdrží atributy.</span><span class="sxs-lookup"><span data-stu-id="0a7d9-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="0a7d9-107">Jedna z hodnot fronty definovaných v bude vrácenou hodnotou [corsymvarflag –](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="0a7d9-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a7d9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a7d9-108">Return Value</span></span>  
 <span data-ttu-id="0a7d9-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="0a7d9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a7d9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a7d9-110">Requirements</span></span>  
 <span data-ttu-id="0a7d9-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0a7d9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7d9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a7d9-112">See also</span></span>

- [<span data-ttu-id="0a7d9-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a7d9-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
