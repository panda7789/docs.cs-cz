---
title: ISymUnmanagedVariable::GetAddressKind – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b5fd3c5e5a7a706929af849ec3a66dd6c41b3bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778295"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="c8956-102">ISymUnmanagedVariable::GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="c8956-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="c8956-103">Získá druh adresu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="c8956-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8956-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8956-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8956-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8956-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c8956-106">[out] Ukazatel `ULONG32` , který přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c8956-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="c8956-107">Možné hodnoty jsou definovány v [corsymaddrkind –](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="c8956-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8956-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8956-108">Return Value</span></span>  
 <span data-ttu-id="c8956-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c8956-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8956-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8956-110">Requirements</span></span>  
 <span data-ttu-id="c8956-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c8956-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8956-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8956-112">See also</span></span>

- [<span data-ttu-id="c8956-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8956-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
