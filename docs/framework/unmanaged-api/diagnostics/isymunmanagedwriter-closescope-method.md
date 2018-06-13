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
ms.openlocfilehash: a11f689f1fa93e1122ffcc78187c4287db7ea534
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427021"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="ab600-102">ISymUnmanagedWriter::CloseScope – metoda</span><span class="sxs-lookup"><span data-stu-id="ab600-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="ab600-103">Zavře aktuální lexikální obor.</span><span class="sxs-lookup"><span data-stu-id="ab600-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab600-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab600-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab600-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab600-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="ab600-106">[v] Posun od začátku metodu bodu na konci posledního instrukce v oboru lexikální v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ab600-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab600-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab600-107">Return Value</span></span>  
 <span data-ttu-id="ab600-108">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="ab600-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab600-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab600-109">Remarks</span></span>  
 <span data-ttu-id="ab600-110">Jakmile je uzavřený obor, může být definováno žádné další proměnné v něm.</span><span class="sxs-lookup"><span data-stu-id="ab600-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="ab600-111">[Isymunmanagedwriter::openscope –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) vrátí identifikátor neprůhledného obor, který lze použít s [isymunmanagedwriter::setscoperange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování oboru později je počáteční a koncové posunutí.</span><span class="sxs-lookup"><span data-stu-id="ab600-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="ab600-112">V takovém případě posunutí předaný `ISymUnmanagedWriter::OpenScope` a `ISymUnmanagedWriter::CloseScope` jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="ab600-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="ab600-113">Identifikátory oboru jsou platné pouze v aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="ab600-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab600-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab600-114">Requirements</span></span>  
 <span data-ttu-id="ab600-115">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab600-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab600-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab600-116">See Also</span></span>  
 [<span data-ttu-id="ab600-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab600-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
