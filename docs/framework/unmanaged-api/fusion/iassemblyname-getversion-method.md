---
title: IAssemblyName::GetVersion – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: c0a43dc1640bdaa0ae104832eb4d1f8eb15b0392
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134333"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="915f5-102">IAssemblyName::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="915f5-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="915f5-103">Získá informace o verzi sestavení, na které odkazuje tento objekt [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="915f5-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="915f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="915f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="915f5-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="915f5-106">mimo Horní 32 bitů verze</span><span class="sxs-lookup"><span data-stu-id="915f5-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="915f5-107">mimo Dolní 32 bitů verze</span><span class="sxs-lookup"><span data-stu-id="915f5-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915f5-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="915f5-108">Requirements</span></span>  
 <span data-ttu-id="915f5-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="915f5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915f5-110">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="915f5-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="915f5-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915f5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="915f5-112">See also</span></span>

- [<span data-ttu-id="915f5-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="915f5-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
