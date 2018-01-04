---
title: "IAssemblyCache::QueryAssemblyInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.QueryAssemblyInfo
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66e09f805b120239eef764b8cd61835e713e236c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="fbc6b-102">IAssemblyCache::QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="fbc6b-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="fbc6b-103">Získá požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbc6b-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc6b-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbc6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbc6b-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="fbc6b-106">[v] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="fbc6b-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="fbc6b-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="fbc6b-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="fbc6b-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="fbc6b-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="fbc6b-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="fbc6b-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="fbc6b-110">[v] Název sestavení, pro které budou načtena data.</span><span class="sxs-lookup"><span data-stu-id="fbc6b-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="fbc6b-111">[ve out] [Assembly_info –](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) struktura, která obsahuje data o sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbc6b-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc6b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbc6b-112">Requirements</span></span>  
 <span data-ttu-id="fbc6b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc6b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc6b-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fbc6b-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fbc6b-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc6b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc6b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbc6b-116">See Also</span></span>  
 [<span data-ttu-id="fbc6b-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbc6b-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
