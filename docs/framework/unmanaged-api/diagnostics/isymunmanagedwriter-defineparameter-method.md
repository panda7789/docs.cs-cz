---
title: ISymUnmanagedWriter::DefineParameter – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6b01abc16334dbe091e7586efcce1c3e390a64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426972"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="1dff1-102">ISymUnmanagedWriter::DefineParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="1dff1-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="1dff1-103">Definuje jeden parametr v aktuální metoda.</span><span class="sxs-lookup"><span data-stu-id="1dff1-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="1dff1-104">Typ parametru jsou převzaty z parametru pozici (pořadí) v rámci signatury metody.</span><span class="sxs-lookup"><span data-stu-id="1dff1-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="1dff1-105">Pokud parametry jsou definované v metadatech pro dané metody, nemáte se znovu definovat pomocí této metody.</span><span class="sxs-lookup"><span data-stu-id="1dff1-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="1dff1-106">Symbol čtečky musí zkontrolovat běžná metadata pro parametry před zaškrtnutím úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="1dff1-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dff1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dff1-107">Syntax</span></span>  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1dff1-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dff1-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1dff1-109">[v] Název parametru.</span><span class="sxs-lookup"><span data-stu-id="1dff1-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1dff1-110">[v] Atributy parametru.</span><span class="sxs-lookup"><span data-stu-id="1dff1-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="1dff1-111">[v] Parametr podpis.</span><span class="sxs-lookup"><span data-stu-id="1dff1-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1dff1-112">[v] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="1dff1-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1dff1-113">[v] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1dff1-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1dff1-114">[v] Druhý adresu pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1dff1-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1dff1-115">[v] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="1dff1-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dff1-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1dff1-116">Return Value</span></span>  
 <span data-ttu-id="1dff1-117">S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="1dff1-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dff1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dff1-118">Requirements</span></span>  
 <span data-ttu-id="1dff1-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1dff1-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dff1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1dff1-120">See Also</span></span>  
 [<span data-ttu-id="1dff1-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dff1-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
