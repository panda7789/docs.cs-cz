---
title: IAssemblyName::GetName – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe0b465d0e15fadde48c2278aa367632bda3f9ef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473819"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="ea5f9-102">IAssemblyName::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="ea5f9-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="ea5f9-103">Získá název jednoduchý a nešifrované sestavení odkazuje situace [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="ea5f9-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea5f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea5f9-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea5f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea5f9-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="ea5f9-106">[out v] Velikost `pwzName` v široké znaky, jako je znak, který ukončovací znak null.</span><span class="sxs-lookup"><span data-stu-id="ea5f9-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="ea5f9-107">[out] Vyrovnávací paměti, která bude uchovávat název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ea5f9-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea5f9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea5f9-108">Requirements</span></span>  
 <span data-ttu-id="ea5f9-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea5f9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea5f9-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ea5f9-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ea5f9-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea5f9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5f9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea5f9-112">See also</span></span>
- [<span data-ttu-id="ea5f9-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea5f9-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
