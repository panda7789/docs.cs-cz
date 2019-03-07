---
title: IMetaDataTables2::GetMetaDataStreamInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57fa18df1baece984a745725dba614e8c4bb1450
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471449"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="8ff67-102">IMetaDataTables2::GetMetaDataStreamInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="8ff67-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="8ff67-103">Získá název, velikost a obsah služby stream metadat v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="8ff67-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ff67-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ff67-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="8ff67-106">[in] Index datového proudu požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="8ff67-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="8ff67-107">[out] Ukazatel na název datového proudu.</span><span class="sxs-lookup"><span data-stu-id="8ff67-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="8ff67-108">[out] Ukazatel na datový proud metadat.</span><span class="sxs-lookup"><span data-stu-id="8ff67-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="8ff67-109">[out] Velikost v bajtech, z `ppv`.</span><span class="sxs-lookup"><span data-stu-id="8ff67-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff67-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ff67-110">Requirements</span></span>  
 <span data-ttu-id="8ff67-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff67-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ff67-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ff67-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ff67-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ff67-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff67-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ff67-115">See also</span></span>
- [<span data-ttu-id="8ff67-116">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ff67-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="8ff67-117">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ff67-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
