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
ms.openlocfilehash: b512389078ab022208c4b163edc8501a900669ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400361"
---
# <a name="init-method"></a><span data-ttu-id="fb2aa-102">Init – metoda</span><span class="sxs-lookup"><span data-stu-id="fb2aa-102">Init Method</span></span>
<span data-ttu-id="fb2aa-103">Připraví objekty implementace [ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) pro použití.</span><span class="sxs-lookup"><span data-stu-id="fb2aa-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb2aa-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb2aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb2aa-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="fb2aa-106">[Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ukazatel na enumenátor metadat.</span><span class="sxs-lookup"><span data-stu-id="fb2aa-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="fb2aa-107">[Imetadataerror – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ukazatel na volitelné rozhraní pro zpracování chyby.</span><span class="sxs-lookup"><span data-stu-id="fb2aa-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb2aa-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb2aa-108">Return Value</span></span>  
 <span data-ttu-id="fb2aa-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="fb2aa-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb2aa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb2aa-110">Requirements</span></span>  
 <span data-ttu-id="fb2aa-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="fb2aa-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2aa-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb2aa-112">See Also</span></span>  
 [<span data-ttu-id="fb2aa-113">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb2aa-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="fb2aa-114">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb2aa-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="fb2aa-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="fb2aa-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
