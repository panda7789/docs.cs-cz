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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097457"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="13e6e-102">IMetaDataTables::GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="13e6e-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="13e6e-103">Získá velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="13e6e-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13e6e-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13e6e-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="13e6e-106">[out] Ukazatel na velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="13e6e-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e6e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13e6e-107">Requirements</span></span>  
 <span data-ttu-id="13e6e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e6e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e6e-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13e6e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13e6e-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13e6e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13e6e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e6e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e6e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13e6e-112">See also</span></span>

- [<span data-ttu-id="13e6e-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13e6e-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="13e6e-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13e6e-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
