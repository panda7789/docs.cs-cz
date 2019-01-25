---
title: ISymUnmanagedWriter::CloseScope – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e33d69e319d7817a54dca76526b6c3ee9bb6384f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729967"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="c2609-102">ISymUnmanagedWriter::CloseScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c2609-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="c2609-103">Zavře aktuální lexikálním rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c2609-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2609-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2609-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2609-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2609-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="c2609-106">[in] Posun od začátku metody bod na konci posledního instrukce v lexikálním rozsahu, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c2609-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2609-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2609-107">Return Value</span></span>  
 <span data-ttu-id="c2609-108">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="c2609-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2609-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2609-109">Remarks</span></span>  
 <span data-ttu-id="c2609-110">Po zavření obor žádné další proměnné lze definovat v něm.</span><span class="sxs-lookup"><span data-stu-id="c2609-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="c2609-111">[Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí neprůhledný oboru identifikátor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) a později určete obor je počáteční a koncové odsazení.</span><span class="sxs-lookup"><span data-stu-id="c2609-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="c2609-112">V takovém případě posunutí předán `ISymUnmanagedWriter::OpenScope` a `ISymUnmanagedWriter::CloseScope` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="c2609-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="c2609-113">Identifikátory oboru jsou platné pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="c2609-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2609-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2609-114">Requirements</span></span>  
 <span data-ttu-id="c2609-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c2609-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2609-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2609-116">See also</span></span>
- [<span data-ttu-id="c2609-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2609-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
