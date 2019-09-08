---
title: CreateAssemblyCache – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c855d6f85c3cbfa6d81a1fbce3ef5b83abb3f583
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795404"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="489fe-102">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="489fe-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="489fe-103">Získá ukazatel na novou instanci [IAssemblyCache](iassemblycache-interface.md) , která představuje globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="489fe-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="489fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="489fe-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="489fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="489fe-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="489fe-106">mimo Vrácený `IAssemblyCache` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="489fe-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="489fe-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="489fe-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="489fe-108">`dwReserved`musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="489fe-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="489fe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="489fe-109">Requirements</span></span>  
 <span data-ttu-id="489fe-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="489fe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="489fe-111">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="489fe-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="489fe-112">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="489fe-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="489fe-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="489fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489fe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="489fe-114">See also</span></span>

- [<span data-ttu-id="489fe-115">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="489fe-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="489fe-116">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="489fe-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="489fe-117">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="489fe-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
