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
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426948"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="cc39d-102">ISymUnmanagedVariable::GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="cc39d-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="cc39d-103">Získá druh adresu tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="cc39d-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc39d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc39d-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc39d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc39d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cc39d-106">[out] Ukazatel na `ULONG32` která přijme hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cc39d-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="cc39d-107">Možné hodnoty jsou definovány v [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="cc39d-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc39d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc39d-108">Return Value</span></span>  
 <span data-ttu-id="cc39d-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cc39d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc39d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc39d-110">Requirements</span></span>  
 <span data-ttu-id="cc39d-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc39d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc39d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc39d-112">See Also</span></span>  
 [<span data-ttu-id="cc39d-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc39d-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
