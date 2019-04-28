---
title: CreateAssemblyNameObject – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd8609bedcea28c1cb8559d378b5e171f3ad568e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669875"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="d6386-102">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="d6386-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="d6386-103">Získá ukazatel rozhraní k [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="d6386-103">Gets an interface pointer to an [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6386-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6386-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6386-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6386-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="d6386-106">[out] Vrácený `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="d6386-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="d6386-107">[in] Název sestavení, pro který chcete vytvořit nový `IAssemblyName` instance.</span><span class="sxs-lookup"><span data-stu-id="d6386-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d6386-108">[in] Příznaky pro předání do konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="d6386-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d6386-109">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d6386-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d6386-110">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d6386-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6386-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6386-111">Requirements</span></span>  
 <span data-ttu-id="d6386-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6386-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6386-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d6386-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6386-114">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6386-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6386-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6386-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6386-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6386-116">See also</span></span>

- [<span data-ttu-id="d6386-117">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6386-117">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="d6386-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="d6386-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
