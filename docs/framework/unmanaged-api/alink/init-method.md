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
ms.openlocfilehash: 999f572d27f75094ecc72c59acee7d35f86d5342
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="init-method"></a><span data-ttu-id="29f95-102">Init – metoda</span><span class="sxs-lookup"><span data-stu-id="29f95-102">Init Method</span></span>
<span data-ttu-id="29f95-103">Připraví objekty implementace [ialink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) pro použití.</span><span class="sxs-lookup"><span data-stu-id="29f95-103">Prepares objects implementing the [IALink Interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md) for use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f95-104">Syntax</span></span>  
  
```  
HRESULT Init(  
    IMetaDataDispenserEx* pDispenser,  
    IMetaDataError* pErrorHandler  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29f95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29f95-105">Parameters</span></span>  
 `pDispenser`  
 <span data-ttu-id="29f95-106">[Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) ukazatel na enumenátor metadat.</span><span class="sxs-lookup"><span data-stu-id="29f95-106">[IMetaDataDispenserEx Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md) pointer to the metadata dispenser.</span></span>  
  
 `pErrorHandler`  
 <span data-ttu-id="29f95-107">[Imetadataerror – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) ukazatel na volitelné rozhraní pro zpracování chyby.</span><span class="sxs-lookup"><span data-stu-id="29f95-107">[IMetaDataError Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) pointer to an optional error handling interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29f95-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29f95-108">Return Value</span></span>  
 <span data-ttu-id="29f95-109">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="29f95-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f95-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29f95-110">Requirements</span></span>  
 <span data-ttu-id="29f95-111">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="29f95-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f95-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="29f95-112">See Also</span></span>  
 [<span data-ttu-id="29f95-113">Ialink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29f95-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="29f95-114">Ialink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29f95-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="29f95-115">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="29f95-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
