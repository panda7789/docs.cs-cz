---
title: ITypeName::GetAssemblyName – metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
ms.openlocfilehash: de89f20842ab505e40ee0e9795774a92a7d5f1a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102669"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="de55a-102">ITypeName::GetAssemblyName – metoda</span><span class="sxs-lookup"><span data-stu-id="de55a-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="de55a-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="de55a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de55a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de55a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="de55a-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de55a-105">Requirements</span></span>  
 <span data-ttu-id="de55a-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de55a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de55a-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="de55a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de55a-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="de55a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de55a-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de55a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de55a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de55a-110">See also</span></span>

- [<span data-ttu-id="de55a-111">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="de55a-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
