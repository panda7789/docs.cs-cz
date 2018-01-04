---
title: "ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineGlobalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 617e3f03f4b1c126a56b47db34ec7044bea8c58b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="b0a17-102">ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b0a17-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="b0a17-103">Definuje jeden globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0a17-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0a17-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b0a17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0a17-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b0a17-106">[v] Globální název proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0a17-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b0a17-107">[v] Globální proměnné atributy.</span><span class="sxs-lookup"><span data-stu-id="b0a17-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b0a17-108">[v] Podpis tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="b0a17-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b0a17-109">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="b0a17-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b0a17-110">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="b0a17-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b0a17-111">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="b0a17-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b0a17-112">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="b0a17-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0a17-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a17-113">Return Value</span></span>  
 <span data-ttu-id="b0a17-114">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="b0a17-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0a17-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0a17-115">Requirements</span></span>  
 <span data-ttu-id="b0a17-116">**Záhlaví:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="b0a17-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a17-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0a17-117">See Also</span></span>  
 [<span data-ttu-id="b0a17-118">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0a17-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="b0a17-119">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="b0a17-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
