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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125824"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="eca82-102">IMetaDataTables::GetNumTables – metoda</span><span class="sxs-lookup"><span data-stu-id="eca82-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="eca82-103">Získá počet tabulek v rámci aktuálního `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="eca82-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca82-104">Syntax</span></span>  
  
```  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eca82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eca82-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="eca82-106">[out] Ukazatel na počet tabulek v rámci aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="eca82-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca82-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eca82-107">Requirements</span></span>  
 <span data-ttu-id="eca82-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca82-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca82-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eca82-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eca82-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eca82-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="eca82-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="eca82-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eca82-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eca82-112">See also</span></span>

- [<span data-ttu-id="eca82-113">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca82-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="eca82-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca82-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
