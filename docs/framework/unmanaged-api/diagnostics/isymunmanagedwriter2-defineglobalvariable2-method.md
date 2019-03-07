---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 067be401b793c227d8b5caa2706f84a59d3a09df
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499040"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="f7ba9-102">ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f7ba9-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="f7ba9-103">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7ba9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7ba9-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7ba9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7ba9-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f7ba9-106">[in] Název globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f7ba9-107">[in] Globální proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="f7ba9-108">[in] Metadata token podpisu.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f7ba9-109">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f7ba9-110">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f7ba9-111">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f7ba9-112">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7ba9-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7ba9-113">Return Value</span></span>  
 <span data-ttu-id="f7ba9-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="f7ba9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7ba9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7ba9-115">Requirements</span></span>  
 <span data-ttu-id="f7ba9-116">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="f7ba9-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ba9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7ba9-117">See also</span></span>
- [<span data-ttu-id="f7ba9-118">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7ba9-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="f7ba9-119">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="f7ba9-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
