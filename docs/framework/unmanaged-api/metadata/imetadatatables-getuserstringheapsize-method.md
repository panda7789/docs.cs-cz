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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645176"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="9c943-102">IMetaDataTables::GetUserStringHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9c943-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="9c943-103">Získá velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="9c943-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c943-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c943-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c943-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c943-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="9c943-106">[out] Ukazatel na velikost v bajtech, řetězec haldy uživatele.</span><span class="sxs-lookup"><span data-stu-id="9c943-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c943-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c943-107">Requirements</span></span>  
 <span data-ttu-id="9c943-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c943-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c943-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c943-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c943-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c943-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c943-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c943-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c943-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c943-112">See also</span></span>

- [<span data-ttu-id="9c943-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c943-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9c943-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c943-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
