---
title: IMetaDataEmit2::SaveDeltaToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31bed2019eef5a37e1086624afdae3e8f2c58632
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119207"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="fcfcf-102">IMetaDataEmit2::SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="fcfcf-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="fcfcf-103">Uloží změny z aktuální relace edit-and-continue do zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fcfcf-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcfcf-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcfcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcfcf-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="fcfcf-106">[in] Ukazatel rozhraní k zapisovatelné proud, do kterého chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="fcfcf-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="fcfcf-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="fcfcf-107">[in] Reserved.</span></span> <span data-ttu-id="fcfcf-108">Tato hodnota musí být nula.</span><span class="sxs-lookup"><span data-stu-id="fcfcf-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfcf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcfcf-109">Requirements</span></span>  
 <span data-ttu-id="fcfcf-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfcf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfcf-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fcfcf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fcfcf-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcfcf-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fcfcf-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fcfcf-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fcfcf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcfcf-114">See also</span></span>

- [<span data-ttu-id="fcfcf-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcfcf-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="fcfcf-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcfcf-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
