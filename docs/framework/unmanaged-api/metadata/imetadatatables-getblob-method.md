---
title: IMetaDataTables::GetBlob – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa631721965123c4427a5d1ff2e0cec2a1ab2395
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637678"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="32d0c-102">IMetaDataTables::GetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="32d0c-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="32d0c-103">Získá ukazatel na binární rozsáhlý objekt (BLOB) na zadaný sloupec indexu.</span><span class="sxs-lookup"><span data-stu-id="32d0c-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32d0c-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32d0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32d0c-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="32d0c-106">[in] Adresa paměti, ze kterého chcete získat `ppData`.</span><span class="sxs-lookup"><span data-stu-id="32d0c-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="32d0c-107">[out] Ukazatel na velikost v bajtech, z `ppData`.</span><span class="sxs-lookup"><span data-stu-id="32d0c-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="32d0c-108">[out] Načte ukazatel na ukazatel na binární data.</span><span class="sxs-lookup"><span data-stu-id="32d0c-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d0c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32d0c-109">Requirements</span></span>  
 <span data-ttu-id="32d0c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32d0c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32d0c-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32d0c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32d0c-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32d0c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32d0c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32d0c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d0c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32d0c-114">See also</span></span>
- [<span data-ttu-id="32d0c-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32d0c-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="32d0c-116">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32d0c-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
