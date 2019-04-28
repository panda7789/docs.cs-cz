---
title: ISymUnmanagedWriter::SetScopeRange – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d7fe8f36c7a5dbe6e715402fd7253092b64e68e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650749"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="dba00-102">ISymUnmanagedWriter::SetScopeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="dba00-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="dba00-103">Definuje rozsah pro zadaný obor lexikální posunu.</span><span class="sxs-lookup"><span data-stu-id="dba00-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="dba00-104">Obor se stane novou aktuální obor a vloženo do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="dba00-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="dba00-105">Obory musí tvořit hierarchii.</span><span class="sxs-lookup"><span data-stu-id="dba00-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="dba00-106">Na stejné úrovni nemohou překrývat.</span><span class="sxs-lookup"><span data-stu-id="dba00-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba00-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dba00-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba00-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="dba00-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="dba00-109">[in] Identifikátor rozsahu pro obor.</span><span class="sxs-lookup"><span data-stu-id="dba00-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="dba00-110">[in] Posun v bajtech, první instrukce v lexikálním rozsahu od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="dba00-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="dba00-111">[in] Posun v bajtech, která je poslední instrukce v lexikálním rozsahu od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="dba00-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dba00-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dba00-112">Return Value</span></span>  
 <span data-ttu-id="dba00-113">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="dba00-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba00-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dba00-114">Remarks</span></span>  
 <span data-ttu-id="dba00-115">[Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí neprůhledný oboru identifikátor, který lze použít s `ISymUnmanagedWriter::SetScopeRange` a určete obor je počáteční a koncové posunutí později.</span><span class="sxs-lookup"><span data-stu-id="dba00-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="dba00-116">V takovém případě posunutí předán `ISymUnmanagedWriter::OpenScope` a [isymunmanagedwriter::closescope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="dba00-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="dba00-117">Identifikátory obor platí pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="dba00-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba00-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dba00-118">Requirements</span></span>  
 <span data-ttu-id="dba00-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dba00-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba00-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dba00-120">See also</span></span>

- [<span data-ttu-id="dba00-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dba00-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
