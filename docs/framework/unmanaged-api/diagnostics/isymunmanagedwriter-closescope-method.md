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
ms.openlocfilehash: e2e911fb1d737ebb6b2106c89ac11335788ace4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501726"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="30a1e-102">ISymUnmanagedWriter::CloseScope – metoda</span><span class="sxs-lookup"><span data-stu-id="30a1e-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="30a1e-103">Zavře aktuální lexikální obor.</span><span class="sxs-lookup"><span data-stu-id="30a1e-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30a1e-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30a1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30a1e-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="30a1e-106">pro Posun od začátku metody bodu na konci poslední instrukce v lexikálním oboru v bajtech.</span><span class="sxs-lookup"><span data-stu-id="30a1e-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30a1e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="30a1e-107">Return Value</span></span>  
 <span data-ttu-id="30a1e-108">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="30a1e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30a1e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30a1e-109">Remarks</span></span>  
 <span data-ttu-id="30a1e-110">Jakmile je obor uzavřen, nelze v něm definovat žádné další proměnné.</span><span class="sxs-lookup"><span data-stu-id="30a1e-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="30a1e-111">[ISymUnmanagedWriter:: OpenScope –](isymunmanagedwriter-openscope-method.md) vrátí neprůhledný identifikátor oboru, který lze použít s [ISymUnmanagedWriter:: SetScopeRange –](isymunmanagedwriter-setscoperange-method.md) pro pozdější definování počátečního a koncového posunu oboru.</span><span class="sxs-lookup"><span data-stu-id="30a1e-111">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="30a1e-112">V tomto případě jsou posunutí předaná do `ISymUnmanagedWriter::OpenScope` a `ISymUnmanagedWriter::CloseScope` ignorována.</span><span class="sxs-lookup"><span data-stu-id="30a1e-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="30a1e-113">Identifikátory oboru jsou platné pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="30a1e-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30a1e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30a1e-114">Requirements</span></span>  
 <span data-ttu-id="30a1e-115">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="30a1e-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a1e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30a1e-116">See also</span></span>

- [<span data-ttu-id="30a1e-117">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30a1e-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
