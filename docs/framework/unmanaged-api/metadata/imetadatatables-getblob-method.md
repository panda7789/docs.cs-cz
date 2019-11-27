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
ms.openlocfilehash: f5a736d80f36afb8d0a643d4a4e36c9abff01995
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445438"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="cb809-102">IMetaDataTables::GetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="cb809-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="cb809-103">Získá ukazatel na binární rozsáhlý objekt (BLOB) v zadaném indexu sloupce.</span><span class="sxs-lookup"><span data-stu-id="cb809-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb809-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb809-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb809-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb809-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="cb809-106">pro Adresa paměti, ze které se má získat `ppData`</span><span class="sxs-lookup"><span data-stu-id="cb809-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="cb809-107">mimo Ukazatel na velikost `ppData`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="cb809-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="cb809-108">mimo Ukazatel na ukazatel na načtená binární data.</span><span class="sxs-lookup"><span data-stu-id="cb809-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb809-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb809-109">Requirements</span></span>  
 <span data-ttu-id="cb809-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb809-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb809-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb809-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb809-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="cb809-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb809-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb809-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb809-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb809-114">See also</span></span>

- [<span data-ttu-id="cb809-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb809-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="cb809-116">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb809-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
