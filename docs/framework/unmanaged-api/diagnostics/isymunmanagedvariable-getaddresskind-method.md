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
ms.openlocfilehash: 4d2de38e5e506873a6db262dcec19c7af9d8a0d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446090"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="fa9c2-102">ISymUnmanagedVariable::GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="fa9c2-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="fa9c2-103">Získá typ adresy této proměnné.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa9c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa9c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa9c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa9c2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fa9c2-106">mimo Ukazatel na `ULONG32`, který přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="fa9c2-107">Možné hodnoty jsou definovány ve výčtu [CorSymAddrKind –](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="fa9c2-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa9c2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa9c2-108">Return Value</span></span>  
 <span data-ttu-id="fa9c2-109">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa9c2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa9c2-110">Requirements</span></span>  
 <span data-ttu-id="fa9c2-111">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fa9c2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9c2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa9c2-112">See also</span></span>

- [<span data-ttu-id="fa9c2-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa9c2-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
