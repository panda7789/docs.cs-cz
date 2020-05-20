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
ms.openlocfilehash: 4008b2a7d785781da5f35b3dc1e564487cb8e760
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609778"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="3b5c6-102">ISymUnmanagedWriter::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="3b5c6-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="3b5c6-103">Otevře nový lexikální obor v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="3b5c6-104">Rozsah se projeví jako nový aktuální obor a je vložen do zásobníku oborů.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="3b5c6-105">Obory musí tvořit hierarchii.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="3b5c6-106">Na stejné úrovni není dovoleno překrývat.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5c6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b5c6-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b5c6-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b5c6-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="3b5c6-109">pro Posun první instrukce v lexikálním rozsahu, v bajtech, od začátku metody.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3b5c6-110">mimo Ukazatel na `ULONG32` , který přijímá identifikátor oboru.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b5c6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3b5c6-111">Return Value</span></span>  
 <span data-ttu-id="3b5c6-112">S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b5c6-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b5c6-113">Remarks</span></span>  
 <span data-ttu-id="3b5c6-114">`ISymUnmanagedWriter::OpenScope`Vrátí neprůhledný identifikátor oboru, který lze použít s [ISymUnmanagedWriter:: SetScopeRange –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) k definování počátečního a koncového posunu oboru v pozdějším čase.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="3b5c6-115">V tomto případě jsou posunutí předaná do `ISymUnmanagedWriter::OpenScope` a [ISymUnmanagedWriter:: CloseScope –](isymunmanagedwriter-closescope-method.md) ignorována.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="3b5c6-116">Identifikátory oboru jsou platné pouze v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="3b5c6-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b5c6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b5c6-117">Requirements</span></span>  
 <span data-ttu-id="3b5c6-118">**Hlavička:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3b5c6-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5c6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b5c6-119">See also</span></span>

- [<span data-ttu-id="3b5c6-120">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b5c6-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
