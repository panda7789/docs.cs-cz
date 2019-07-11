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
ms.openlocfilehash: a2c5c3bbbcf3cf4b87a5f68006c1625666d13926
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753886"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="9ad55-102">IAssemblyName::GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="9ad55-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="9ad55-103">Získá název jednoduchý a nešifrované sestavení odkazuje situace [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="9ad55-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ad55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ad55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ad55-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="9ad55-106">[out v] Velikost `pwzName` v široké znaky, jako je znak, který ukončovací znak null.</span><span class="sxs-lookup"><span data-stu-id="9ad55-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="9ad55-107">[out] Vyrovnávací paměti, která bude uchovávat název odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ad55-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ad55-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ad55-108">Requirements</span></span>  
 <span data-ttu-id="9ad55-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad55-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad55-110">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9ad55-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9ad55-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad55-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad55-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ad55-112">See also</span></span>

- [<span data-ttu-id="9ad55-113">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ad55-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
