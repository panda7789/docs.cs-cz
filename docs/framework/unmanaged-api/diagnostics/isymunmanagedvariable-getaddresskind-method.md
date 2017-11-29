---
title: "ISymUnmanagedVariable::GetAddressKind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 930b55c98609e5f3bc33f30da766c4556fbe5512
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="10277-102">ISymUnmanagedVariable::GetAddressKind – metoda</span><span class="sxs-lookup"><span data-stu-id="10277-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="10277-103">Získá druh adresu tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="10277-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10277-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10277-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10277-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="10277-106">[out] Ukazatel na `ULONG32` která přijme hodnotu.</span><span class="sxs-lookup"><span data-stu-id="10277-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="10277-107">Možné hodnoty jsou definovány v [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="10277-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10277-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10277-108">Return Value</span></span>  
 <span data-ttu-id="10277-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="10277-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10277-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10277-110">Requirements</span></span>  
 <span data-ttu-id="10277-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="10277-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10277-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="10277-112">See Also</span></span>  
 [<span data-ttu-id="10277-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10277-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
