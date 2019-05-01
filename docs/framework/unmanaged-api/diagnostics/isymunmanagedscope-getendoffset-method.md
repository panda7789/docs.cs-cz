---
title: ISymUnmanagedScope::GetEndOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e28a351b6d47d14f171b9e760b2fa2c6755e3f8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986179"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="83025-102">ISymUnmanagedScope::GetEndOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="83025-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="83025-103">Získá koncové odsazení pro tento obor.</span><span class="sxs-lookup"><span data-stu-id="83025-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83025-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83025-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83025-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83025-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="83025-106">[out] Ukazatel `ULONG32` , která obdrží koncové odsazení.</span><span class="sxs-lookup"><span data-stu-id="83025-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83025-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83025-107">Return Value</span></span>  
 <span data-ttu-id="83025-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="83025-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83025-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83025-109">Requirements</span></span>  
 <span data-ttu-id="83025-110">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="83025-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83025-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83025-111">See also</span></span>

- [<span data-ttu-id="83025-112">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83025-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="83025-113">GetStartOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="83025-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
