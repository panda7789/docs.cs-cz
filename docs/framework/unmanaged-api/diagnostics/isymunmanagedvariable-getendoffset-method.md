---
title: ISymUnmanagedVariable::GetEndOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0f11614c6fa15034ef5fa3d68e41a936a9ff764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427854"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="5b343-102">ISymUnmanagedVariable::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="5b343-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="5b343-103">Získá posun end této proměnné v rámci jeho nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="5b343-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="5b343-104">Pokud je to místní proměnné v oboru, posun end bude spadat do posuny definované pro obor.</span><span class="sxs-lookup"><span data-stu-id="5b343-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b343-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b343-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b343-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b343-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5b343-107">[out] Ukazatel na `ULONG32` která přijme posun end.</span><span class="sxs-lookup"><span data-stu-id="5b343-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b343-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b343-108">Return Value</span></span>  
 <span data-ttu-id="5b343-109">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="5b343-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b343-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b343-110">Requirements</span></span>  
 <span data-ttu-id="5b343-111">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b343-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b343-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b343-112">See Also</span></span>  
 [<span data-ttu-id="5b343-113">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b343-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="5b343-114">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="5b343-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
