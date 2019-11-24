---
title: IMetaDataTables2::GetMetaDataStorage – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
ms.openlocfilehash: 302e9db3bc683eaa2b65e0b0479de721e07d56db
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442653"
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="e774d-102">IMetaDataTables2::GetMetaDataStorage – metoda</span><span class="sxs-lookup"><span data-stu-id="e774d-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="e774d-103">Gets the size and contents of the metadata stored in the specified section.</span><span class="sxs-lookup"><span data-stu-id="e774d-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e774d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e774d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e774d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e774d-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="e774d-106">[in, out] A pointer to a metadata section.</span><span class="sxs-lookup"><span data-stu-id="e774d-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="e774d-107">[out] The size of the metadata stream.</span><span class="sxs-lookup"><span data-stu-id="e774d-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e774d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e774d-108">Requirements</span></span>  
 <span data-ttu-id="e774d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e774d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e774d-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e774d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e774d-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e774d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e774d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e774d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e774d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e774d-113">See also</span></span>

- [<span data-ttu-id="e774d-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e774d-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [<span data-ttu-id="e774d-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e774d-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
