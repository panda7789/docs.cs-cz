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
ms.openlocfilehash: d0fb35f5d7fec0c79a31cd8d7b77cf2b1c043f60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986073"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="8fde3-102">ISymUnmanagedWriter::DefineParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="8fde3-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="8fde3-103">Definuje jeden parametr v aktuální metodě.</span><span class="sxs-lookup"><span data-stu-id="8fde3-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="8fde3-104">Typ parametru je převzata z pozice parametru (pořadí) v podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="8fde3-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="8fde3-105">Pokud parametry jsou definované v metadatech pro dané metody, není nutné znovu definovat pomocí této metody.</span><span class="sxs-lookup"><span data-stu-id="8fde3-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="8fde3-106">Čtenáři symbolu, musíte zaškrtnout běžná metadata pro parametry před vrácením se změnami úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="8fde3-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fde3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fde3-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8fde3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fde3-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8fde3-109">[in] Název parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="8fde3-110">[in] Atributy parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="8fde3-111">[in] Podpis parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="8fde3-112">[in] Typ adresy.</span><span class="sxs-lookup"><span data-stu-id="8fde3-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="8fde3-113">[in] První adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="8fde3-114">[in] Druhý adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="8fde3-115">[in] Je třetí adresa pro specifikaci parametru.</span><span class="sxs-lookup"><span data-stu-id="8fde3-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fde3-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8fde3-116">Return Value</span></span>  
 <span data-ttu-id="8fde3-117">Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.</span><span class="sxs-lookup"><span data-stu-id="8fde3-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fde3-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fde3-118">Requirements</span></span>  
 <span data-ttu-id="8fde3-119">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8fde3-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fde3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fde3-120">See also</span></span>

- [<span data-ttu-id="8fde3-121">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8fde3-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
