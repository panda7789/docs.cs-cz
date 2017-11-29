---
title: "ITypeNameFactory::ParseTypeName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeNameFactory.ParseTypeName
api_location: mscoree.dll
api_type: COM
f1_keywords: ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f80778196bc23a8cdaa8aff9917265a0ad379c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="80d66-102">ITypeNameFactory::ParseTypeName – metoda</span><span class="sxs-lookup"><span data-stu-id="80d66-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="80d66-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="80d66-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80d66-104">Syntax</span></span>  
  
```  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="80d66-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80d66-105">Requirements</span></span>  
 <span data-ttu-id="80d66-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d66-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d66-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80d66-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80d66-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80d66-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80d66-109">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d66-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d66-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="80d66-110">See Also</span></span>  
 [<span data-ttu-id="80d66-111">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="80d66-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
