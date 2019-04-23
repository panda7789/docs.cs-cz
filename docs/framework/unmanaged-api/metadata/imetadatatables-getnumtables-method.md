---
title: IMetaDataTables::GetNumTables – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ffd9ab9ddb95945744ecf210d0ae1d9d9812ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125824"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="9c6f3-102">IMetaDataTables::GetNumTables – metoda</span><span class="sxs-lookup"><span data-stu-id="9c6f3-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="9c6f3-103">Získá počet tabulek v rámci aktuálního `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="9c6f3-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c6f3-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c6f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c6f3-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="9c6f3-106">[out] Ukazatel na počet tabulek v rámci aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="9c6f3-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c6f3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c6f3-107">Requirements</span></span>  
 <span data-ttu-id="9c6f3-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c6f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c6f3-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c6f3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c6f3-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c6f3-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c6f3-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c6f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6f3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c6f3-112">See also</span></span>

- [<span data-ttu-id="9c6f3-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c6f3-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="9c6f3-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c6f3-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
