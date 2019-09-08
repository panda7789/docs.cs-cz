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
ms.openlocfilehash: 08b9fdee1138becd4cd5a933f96021c470aadf1f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796790"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="9b066-102">IAssemblyCache::QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="9b066-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="9b066-103">Načte požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b066-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b066-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b066-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b066-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b066-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="9b066-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="9b066-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="9b066-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="9b066-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="9b066-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="9b066-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="9b066-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="9b066-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="9b066-110">pro Název sestavení, pro které budou načtena data</span><span class="sxs-lookup"><span data-stu-id="9b066-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="9b066-111">[in, out] Struktura [ASSEMBLY_INFO](assembly-info-structure.md) , která obsahuje data o sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b066-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b066-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b066-112">Requirements</span></span>  
 <span data-ttu-id="9b066-113">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b066-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b066-114">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9b066-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9b066-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b066-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b066-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b066-116">See also</span></span>

- [<span data-ttu-id="9b066-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b066-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
