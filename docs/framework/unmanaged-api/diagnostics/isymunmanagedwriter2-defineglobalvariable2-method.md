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
ms.openlocfilehash: a6e4b323f9e06f2c5dc336af772bdade0db3dea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657438"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="7cca1-102">ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7cca1-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="7cca1-103">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7cca1-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cca1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cca1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="7cca1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cca1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7cca1-106">[in] Název globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="7cca1-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="7cca1-107">[in] Globální proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="7cca1-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="7cca1-108">[in] Metadata token podpisu.</span><span class="sxs-lookup"><span data-stu-id="7cca1-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="7cca1-109">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="7cca1-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="7cca1-110">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="7cca1-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="7cca1-111">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="7cca1-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="7cca1-112">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="7cca1-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cca1-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7cca1-113">Return Value</span></span>  
 <span data-ttu-id="7cca1-114">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="7cca1-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cca1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cca1-115">Requirements</span></span>  
 <span data-ttu-id="7cca1-116">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="7cca1-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cca1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cca1-117">See also</span></span>
- [<span data-ttu-id="7cca1-118">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cca1-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="7cca1-119">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="7cca1-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
