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
ms.openlocfilehash: a54d3cb1bb9abf740c2c9b5a9a8312a9612ae658
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894452"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="54814-102">ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda</span><span class="sxs-lookup"><span data-stu-id="54814-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="54814-103">Definuje jednu globální proměnnou.</span><span class="sxs-lookup"><span data-stu-id="54814-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54814-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54814-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54814-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54814-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="54814-106">pro Název globální proměnné</span><span class="sxs-lookup"><span data-stu-id="54814-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="54814-107">pro Atributy globálních proměnných.</span><span class="sxs-lookup"><span data-stu-id="54814-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="54814-108">pro Token metadat podpisu</span><span class="sxs-lookup"><span data-stu-id="54814-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="54814-109">pro Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="54814-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="54814-110">pro První adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="54814-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="54814-111">pro Druhá adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="54814-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="54814-112">pro Třetí adresa specifikace parametru.</span><span class="sxs-lookup"><span data-stu-id="54814-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54814-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="54814-113">Return Value</span></span>  
 <span data-ttu-id="54814-114">S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="54814-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54814-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54814-115">Requirements</span></span>  
 <span data-ttu-id="54814-116">**Hlaviček** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="54814-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54814-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54814-117">See also</span></span>

- [<span data-ttu-id="54814-118">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54814-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="54814-119">DefineGlobalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="54814-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
