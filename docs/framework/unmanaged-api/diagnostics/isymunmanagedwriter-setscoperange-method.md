---
title: "ISymUnmanagedWriter::SetScopeRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b86df423d53c9fa3a738c603d6cc575add594cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="1f405-102">ISymUnmanagedWriter::SetScopeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1f405-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="1f405-103">Definuje rozsah pro zadaný obor lexikální posunu.</span><span class="sxs-lookup"><span data-stu-id="1f405-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="1f405-104">Obor se stane nový aktuální obor a se posune do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="1f405-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="1f405-105">Obory musí tvořit hierarchie.</span><span class="sxs-lookup"><span data-stu-id="1f405-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="1f405-106">Položky na stejné úrovni nemohou překrývat.</span><span class="sxs-lookup"><span data-stu-id="1f405-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f405-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f405-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f405-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f405-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="1f405-109">[v] Identifikátor oboru pro obor.</span><span class="sxs-lookup"><span data-stu-id="1f405-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="1f405-110">[v] Posun v bajtech je první instrukce v oboru lexikální od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="1f405-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="1f405-111">[v] Posun v bajtech je poslední instrukce v oboru lexikální od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="1f405-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f405-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1f405-112">Return Value</span></span>  
 <span data-ttu-id="1f405-113">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1f405-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f405-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f405-114">Remarks</span></span>  
 <span data-ttu-id="1f405-115">[Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí identifikátor neprůhledného obor, který lze použít s `ISymUnmanagedWriter::SetScopeRange` k definování oboru je počáteční a koncové posunutí později.</span><span class="sxs-lookup"><span data-stu-id="1f405-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="1f405-116">V takovém případě posunutí předaný `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="1f405-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="1f405-117">Identifikátory obor platí pouze v aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="1f405-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f405-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f405-118">Requirements</span></span>  
 <span data-ttu-id="1f405-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f405-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f405-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f405-120">See Also</span></span>  
 [<span data-ttu-id="1f405-121">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f405-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
