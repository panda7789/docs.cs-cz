---
title: ISymUnmanagedWriter::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea6ce91e0651e09fb908d8b8b35811349ac8845
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089429"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="8af66-102">ISymUnmanagedWriter::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="8af66-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="8af66-103">Otevře se nový lexikální rozsah v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="8af66-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="8af66-104">Obor se stane novou aktuální obor a vloženo do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="8af66-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="8af66-105">Obory musí tvořit hierarchii.</span><span class="sxs-lookup"><span data-stu-id="8af66-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="8af66-106">Na stejné úrovni nemohou překrývat.</span><span class="sxs-lookup"><span data-stu-id="8af66-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af66-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8af66-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8af66-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="8af66-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="8af66-109">[in] Posun první instrukce v lexikálním rozsahu, v bajtech od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="8af66-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8af66-110">[out] Ukazatel `ULONG32` , která přijímá identifikátor rozsahu.</span><span class="sxs-lookup"><span data-stu-id="8af66-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8af66-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8af66-111">Return Value</span></span>  
 <span data-ttu-id="8af66-112">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8af66-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8af66-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8af66-113">Remarks</span></span>  
 <span data-ttu-id="8af66-114">`ISymUnmanagedWriter::OpenScope` Vrátí obor neprůhledný identifikátor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) a určete obor je počáteční a koncové posunutí později.</span><span class="sxs-lookup"><span data-stu-id="8af66-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="8af66-115">V takovém případě posunutí předán `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8af66-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="8af66-116">Identifikátory oboru jsou platné pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="8af66-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8af66-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8af66-117">Requirements</span></span>  
 <span data-ttu-id="8af66-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8af66-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af66-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8af66-119">See also</span></span>

- [<span data-ttu-id="8af66-120">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8af66-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
