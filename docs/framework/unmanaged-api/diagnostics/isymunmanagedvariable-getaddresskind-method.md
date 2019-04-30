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
ms.openlocfilehash: eae5b21af3bcdca911ec13067a61bb957d4ae6ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797576"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="dfeee-102">ISymUnmanagedVariable::GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="dfeee-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="dfeee-103">Získá druh adresu této proměnné.</span><span class="sxs-lookup"><span data-stu-id="dfeee-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfeee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfeee-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfeee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfeee-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dfeee-106">[out] Ukazatel `ULONG32` , který přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dfeee-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="dfeee-107">Možné hodnoty jsou definovány v [corsymaddrkind –](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="dfeee-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfeee-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dfeee-108">Return Value</span></span>  
 <span data-ttu-id="dfeee-109">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="dfeee-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfeee-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfeee-110">Requirements</span></span>  
 <span data-ttu-id="dfeee-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dfeee-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfeee-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfeee-112">See also</span></span>

- [<span data-ttu-id="dfeee-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfeee-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
