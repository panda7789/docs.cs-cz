---
title: IAssemblyCache::QueryAssemblyInfo – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81b647032b2e9474e3b4472552ed884cec92ffc3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216410"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="37ba2-102">IAssemblyCache::QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="37ba2-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="37ba2-103">Získá požadovaná data o zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="37ba2-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ba2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37ba2-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37ba2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37ba2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="37ba2-106">[in] Příznaky definované v Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="37ba2-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="37ba2-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="37ba2-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="37ba2-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="37ba2-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="37ba2-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="37ba2-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="37ba2-110">[in] Název sestavení, pro kterou budou načtena data.</span><span class="sxs-lookup"><span data-stu-id="37ba2-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="37ba2-111">[out v] [Assembly_info –](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) strukturu, která obsahuje data o sestavení.</span><span class="sxs-lookup"><span data-stu-id="37ba2-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ba2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37ba2-112">Requirements</span></span>  
 <span data-ttu-id="37ba2-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ba2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ba2-114">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="37ba2-114">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="37ba2-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="37ba2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="37ba2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37ba2-116">See also</span></span>

- [<span data-ttu-id="37ba2-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ba2-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
