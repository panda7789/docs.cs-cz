---
title: "IMetaDataEmit2::SaveDeltaToStream – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4bab7bd9035c0746b7f789925e23b74e2caade6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="92c8b-102">IMetaDataEmit2::SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="92c8b-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="92c8b-103">Uloží změny do zadaného datového proudu z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="92c8b-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c8b-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92c8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92c8b-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="92c8b-106">[v] Ukazatel rozhraní s možností zápisu datového proudu, do které chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="92c8b-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="92c8b-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="92c8b-107">[in] Reserved.</span></span> <span data-ttu-id="92c8b-108">Tato hodnota musí být nula.</span><span class="sxs-lookup"><span data-stu-id="92c8b-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c8b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c8b-109">Requirements</span></span>  
 <span data-ttu-id="92c8b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c8b-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="92c8b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92c8b-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92c8b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92c8b-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c8b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="92c8b-114">See Also</span></span>  
 [<span data-ttu-id="92c8b-115">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92c8b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="92c8b-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92c8b-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
