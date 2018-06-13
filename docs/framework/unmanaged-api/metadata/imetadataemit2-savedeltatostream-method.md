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
ms.openlocfilehash: e9dfd97ce5b9b192b9a2e88e3d7e4f963d929f47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449257"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="d1424-102">IMetaDataEmit2::SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d1424-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="d1424-103">Uloží změny do zadaného datového proudu z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d1424-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1424-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1424-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1424-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1424-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="d1424-106">[v] Ukazatel rozhraní s možností zápisu datového proudu, do které chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="d1424-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d1424-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="d1424-107">[in] Reserved.</span></span> <span data-ttu-id="d1424-108">Tato hodnota musí být nula.</span><span class="sxs-lookup"><span data-stu-id="d1424-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1424-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1424-109">Requirements</span></span>  
 <span data-ttu-id="d1424-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1424-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1424-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1424-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1424-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1424-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1424-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1424-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1424-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1424-114">See Also</span></span>  
 [<span data-ttu-id="d1424-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1424-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="d1424-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1424-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
