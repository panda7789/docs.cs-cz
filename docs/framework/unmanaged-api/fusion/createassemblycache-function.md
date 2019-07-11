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
ms.openlocfilehash: ffeb04ddcec290f899556bf0d8078acfb06707ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778602"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="1a0d5-102">CreateAssemblyCache – funkce</span><span class="sxs-lookup"><span data-stu-id="1a0d5-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="1a0d5-103">Získá ukazatel na novou [iassemblycache –](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance, který představuje globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="1a0d5-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a0d5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a0d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a0d5-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="1a0d5-106">[out] Vrácený `IAssemblyCache` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="1a0d5-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="1a0d5-107">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1a0d5-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1a0d5-108">`dwReserved` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="1a0d5-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0d5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a0d5-109">Requirements</span></span>  
 <span data-ttu-id="1a0d5-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0d5-111">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1a0d5-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1a0d5-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a0d5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a0d5-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0d5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a0d5-114">See also</span></span>

- [<span data-ttu-id="1a0d5-115">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a0d5-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="1a0d5-116">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="1a0d5-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="1a0d5-117">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="1a0d5-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
