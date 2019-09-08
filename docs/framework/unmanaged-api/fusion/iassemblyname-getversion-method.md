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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58919936bdc62d52437f429146f04c66d49294b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796580"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="0ddb9-102">IAssemblyName::GetVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="0ddb9-102">IAssemblyName::GetVersion Method</span></span>
<span data-ttu-id="0ddb9-103">Získá informace o verzi sestavení, na které odkazuje tento objekt [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0ddb9-103">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ddb9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ddb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ddb9-105">Parameters</span></span>  
 `pdwVersionHi`  
 <span data-ttu-id="0ddb9-106">mimo Horní 32 bitů verze</span><span class="sxs-lookup"><span data-stu-id="0ddb9-106">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="0ddb9-107">mimo Dolní 32 bitů verze</span><span class="sxs-lookup"><span data-stu-id="0ddb9-107">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ddb9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ddb9-108">Requirements</span></span>  
 <span data-ttu-id="0ddb9-109">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ddb9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ddb9-110">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0ddb9-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0ddb9-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ddb9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddb9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ddb9-112">See also</span></span>

- [<span data-ttu-id="0ddb9-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ddb9-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
