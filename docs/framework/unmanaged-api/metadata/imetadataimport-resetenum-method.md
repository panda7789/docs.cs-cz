---
title: "IMetaDataImport::ResetEnum – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResetEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2cdb4c00185d152be856a99e1fec9392fd2a4029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="9bfcd-102">IMetaDataImport::ResetEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="9bfcd-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="9bfcd-103">Zadaný čítač obnoví na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="9bfcd-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bfcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bfcd-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bfcd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bfcd-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9bfcd-106">[v] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="9bfcd-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="9bfcd-107">[v] Nové umístění, kam chcete umístit enumerátor.</span><span class="sxs-lookup"><span data-stu-id="9bfcd-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bfcd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bfcd-108">Requirements</span></span>  
 <span data-ttu-id="9bfcd-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bfcd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bfcd-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9bfcd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9bfcd-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bfcd-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9bfcd-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bfcd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfcd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bfcd-113">See Also</span></span>  
 [<span data-ttu-id="9bfcd-114">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bfcd-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9bfcd-115">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bfcd-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
