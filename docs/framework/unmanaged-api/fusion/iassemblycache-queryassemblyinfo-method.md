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
ms.openlocfilehash: e975db68252e866a0bf7898f1c9d3cbe67bbe24f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134581"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="077bd-102">IAssemblyCache::QueryAssemblyInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="077bd-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="077bd-103">Načte požadovaná data o zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="077bd-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="077bd-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="077bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="077bd-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="077bd-106">pro Příznaky definované v Fusion. idl</span><span class="sxs-lookup"><span data-stu-id="077bd-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="077bd-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="077bd-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="077bd-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="077bd-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="077bd-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="077bd-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="077bd-110">pro Název sestavení, pro které budou načtena data</span><span class="sxs-lookup"><span data-stu-id="077bd-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="077bd-111">[in, out] Struktura [ASSEMBLY_INFO](assembly-info-structure.md) , která obsahuje data o sestavení.</span><span class="sxs-lookup"><span data-stu-id="077bd-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="077bd-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="077bd-112">Requirements</span></span>  
 <span data-ttu-id="077bd-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077bd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="077bd-114">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="077bd-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="077bd-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077bd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="077bd-116">See also</span></span>

- [<span data-ttu-id="077bd-117">IAssemblyCache – rozhraní</span><span class="sxs-lookup"><span data-stu-id="077bd-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
