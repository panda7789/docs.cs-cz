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
ms.openlocfilehash: cf6deb4d1420e7b58e1edc7741b683beb591ca5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782105"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="02224-102">IMetaDataTables::GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="02224-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="02224-103">Získá velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="02224-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02224-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02224-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02224-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02224-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="02224-106">[out] Ukazatel na velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="02224-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02224-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02224-107">Requirements</span></span>  
 <span data-ttu-id="02224-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02224-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02224-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02224-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02224-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02224-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02224-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02224-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02224-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02224-112">See also</span></span>

- [<span data-ttu-id="02224-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02224-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="02224-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02224-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
