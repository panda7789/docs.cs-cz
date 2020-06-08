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
ms.openlocfilehash: a1da070f261f224d212d1fba81c287285a54d0d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501689"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="1af1b-102">ISymUnmanagedWriter::SetScopeRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1af1b-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="1af1b-103">Definuje rozsah posunu pro zadaný lexikální obor.</span><span class="sxs-lookup"><span data-stu-id="1af1b-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="1af1b-104">Rozsah se projeví jako nový aktuální obor a je vložen do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="1af1b-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="1af1b-105">Obory musí tvořit hierarchii.</span><span class="sxs-lookup"><span data-stu-id="1af1b-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="1af1b-106">Na stejné úrovni není dovoleno překrývat.</span><span class="sxs-lookup"><span data-stu-id="1af1b-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1af1b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1af1b-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1af1b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1af1b-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="1af1b-109">pro Identifikátor oboru pro obor.</span><span class="sxs-lookup"><span data-stu-id="1af1b-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="1af1b-110">pro Posun v bajtech první instrukce v lexikálním rozsahu od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="1af1b-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="1af1b-111">pro Posun poslední instrukce v lexikálním oboru od začátku metody v bajtech.</span><span class="sxs-lookup"><span data-stu-id="1af1b-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1af1b-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1af1b-112">Return Value</span></span>  
 <span data-ttu-id="1af1b-113">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1af1b-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1af1b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1af1b-114">Remarks</span></span>  
 <span data-ttu-id="1af1b-115">[ISymUnmanagedWriter:: OpenScope –](isymunmanagedwriter-openscope-method.md) vrátí neprůhledný identifikátor oboru, který lze použít s `ISymUnmanagedWriter::SetScopeRange` k definování počátečního a koncového posunu oboru později.</span><span class="sxs-lookup"><span data-stu-id="1af1b-115">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="1af1b-116">V tomto případě jsou posunutí předaná do `ISymUnmanagedWriter::OpenScope` a [ISymUnmanagedWriter:: CloseScope –](isymunmanagedwriter-closescope-method.md) ignorována.</span><span class="sxs-lookup"><span data-stu-id="1af1b-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="1af1b-117">Identifikátory oboru jsou platné pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="1af1b-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1af1b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1af1b-118">Requirements</span></span>  
 <span data-ttu-id="1af1b-119">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1af1b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af1b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1af1b-120">See also</span></span>

- [<span data-ttu-id="1af1b-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1af1b-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
