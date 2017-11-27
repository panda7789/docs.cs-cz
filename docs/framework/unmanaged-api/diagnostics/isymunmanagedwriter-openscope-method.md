---
title: "ISymUnmanagedWriter::OpenScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f56bc14b096b5086db1fc8d046ed699559381fb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="7f144-102">ISymUnmanagedWriter::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="7f144-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="7f144-103">Otevře nové lexikální obor v aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="7f144-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="7f144-104">Obor se stane nový aktuální obor a se posune do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="7f144-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="7f144-105">Obory musí tvořit hierarchie.</span><span class="sxs-lookup"><span data-stu-id="7f144-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="7f144-106">Položky na stejné úrovni nemohou překrývat.</span><span class="sxs-lookup"><span data-stu-id="7f144-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f144-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f144-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f144-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f144-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="7f144-109">[v] Posun první instrukce v oboru lexikální v bajtech, od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="7f144-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7f144-110">[out] Ukazatel na `ULONG32` která přijme identifikátor oboru.</span><span class="sxs-lookup"><span data-stu-id="7f144-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f144-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f144-111">Return Value</span></span>  
 <span data-ttu-id="7f144-112">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7f144-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f144-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f144-113">Remarks</span></span>  
 <span data-ttu-id="7f144-114">`ISymUnmanagedWriter::OpenScope`Vrátí identifikátor neprůhledného obor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování oboru je počáteční a koncové posunutí později.</span><span class="sxs-lookup"><span data-stu-id="7f144-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="7f144-115">V takovém případě posunutí předaný `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="7f144-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="7f144-116">Identifikátory oboru jsou platné pouze v aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="7f144-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f144-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f144-117">Requirements</span></span>  
 <span data-ttu-id="7f144-118">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f144-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f144-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f144-119">See Also</span></span>  
 [<span data-ttu-id="7f144-120">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f144-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
