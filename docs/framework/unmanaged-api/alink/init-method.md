---
title: Init – metoda
ms.date: 03/30/2017
api_name:
- IALink.Init
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- Init
helpviewer_keywords:
- Init method
ms.assetid: e48b5c64-049f-4f93-ad87-d07ae9cd5845
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60602462376543fe934bb3c58bc4988fa8ab34bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119363"
---
# <a name="init-method"></a><span data-ttu-id="5336b-102">Init – metoda</span><span class="sxs-lookup"><span data-stu-id="5336b-102">Init Method</span></span>
<span data-ttu-id="5336b-103">Připraví objekty implementace [ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) pro použití.</span><span class="sxs-lookup"><span data-stu-id="5336b-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5336b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5336b-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5336b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5336b-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="5336b-106">[Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ukazatel na řadič metadat.</span><span class="sxs-lookup"><span data-stu-id="5336b-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="5336b-107">[Imetadataerror – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ukazatel na volitelné rozhraní pro zpracování chyby.</span><span class="sxs-lookup"><span data-stu-id="5336b-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5336b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5336b-108">Return Value</span></span>  
 <span data-ttu-id="5336b-109">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="5336b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5336b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5336b-110">Requirements</span></span>  
 <span data-ttu-id="5336b-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="5336b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5336b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5336b-112">See also</span></span>

- [<span data-ttu-id="5336b-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5336b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5336b-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5336b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5336b-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="5336b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
