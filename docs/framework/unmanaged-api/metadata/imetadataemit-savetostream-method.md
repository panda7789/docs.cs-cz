---
title: IMetaDataEmit::SaveToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f6b5582b96dfc83eed482def2c4c4abfeb33a4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042988"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="a74bf-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="a74bf-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="a74bf-103">Uloží všechna metadata v aktuálním oboru na zadaný `IStream`.</span><span class="sxs-lookup"><span data-stu-id="a74bf-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a74bf-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a74bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a74bf-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="a74bf-106">[in] Zapisovatelný datový proud uložte.</span><span class="sxs-lookup"><span data-stu-id="a74bf-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="a74bf-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="a74bf-107">[in] Reserved.</span></span> <span data-ttu-id="a74bf-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="a74bf-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74bf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a74bf-109">Requirements</span></span>  
 <span data-ttu-id="a74bf-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a74bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74bf-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a74bf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a74bf-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a74bf-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a74bf-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74bf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a74bf-114">See also</span></span>

- [<span data-ttu-id="a74bf-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a74bf-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a74bf-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a74bf-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
