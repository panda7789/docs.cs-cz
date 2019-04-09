---
title: IMetaDataTables::GetUserStringHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d35231e4c36639722635796891056a8902b95940
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097457"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="7d825-102">IMetaDataTables::GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="7d825-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="7d825-103">Získá velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d825-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d825-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d825-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="7d825-106">[out] Ukazatel na velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d825-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d825-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d825-107">Requirements</span></span>  
 <span data-ttu-id="7d825-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d825-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d825-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d825-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7d825-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d825-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7d825-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7d825-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d825-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d825-112">See also</span></span>

- [<span data-ttu-id="7d825-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d825-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="7d825-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d825-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
