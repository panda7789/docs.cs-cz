---
title: "Init – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.Init
api_location: alink.dll
api_type: COM
f1_keywords: Init
helpviewer_keywords: Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19e37a4df8055f14a72a4c9093cd594a234ae80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="init-method"></a><span data-ttu-id="87043-102">Init – metoda</span><span class="sxs-lookup"><span data-stu-id="87043-102">Init Method</span></span>
<span data-ttu-id="87043-103">Připraví objekty implementace [ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) pro použití.</span><span class="sxs-lookup"><span data-stu-id="87043-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87043-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87043-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87043-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="87043-106">[Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ukazatel na enumenátor metadat.</span><span class="sxs-lookup"><span data-stu-id="87043-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="87043-107">[Imetadataerror – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ukazatel na volitelné rozhraní pro zpracování chyby.</span><span class="sxs-lookup"><span data-stu-id="87043-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87043-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="87043-108">Return Value</span></span>  
 <span data-ttu-id="87043-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="87043-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87043-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87043-110">Requirements</span></span>  
 <span data-ttu-id="87043-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="87043-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87043-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="87043-112">See Also</span></span>  
 [<span data-ttu-id="87043-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87043-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="87043-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87043-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="87043-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="87043-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
