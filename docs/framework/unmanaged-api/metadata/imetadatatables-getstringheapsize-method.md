---
title: IMetaDataTables::GetStringHeapSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fe6559eca2fef1c9481c8996b19ffb8a08c6019
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049749"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="d97d2-102">IMetaDataTables::GetStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d97d2-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="d97d2-103">Získá velikost v bajtech, řetězec haldy.</span><span class="sxs-lookup"><span data-stu-id="d97d2-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d97d2-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d97d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d97d2-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="d97d2-106">[out] Ukazatel na velikost v bajtech, řetězec haldy.</span><span class="sxs-lookup"><span data-stu-id="d97d2-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d97d2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d97d2-107">Requirements</span></span>  
 <span data-ttu-id="d97d2-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97d2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97d2-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d97d2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d97d2-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d97d2-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d97d2-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d97d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97d2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d97d2-112">See also</span></span>

- [<span data-ttu-id="d97d2-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d97d2-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d97d2-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d97d2-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
