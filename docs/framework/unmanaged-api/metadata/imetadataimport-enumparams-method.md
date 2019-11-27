---
title: IMetaDataImport::EnumParams – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: e5fa3647c86d97730e7ad6a2576dd34af75251d6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433956"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="be19d-102">IMetaDataImport::EnumParams – metoda</span><span class="sxs-lookup"><span data-stu-id="be19d-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="be19d-103">Vytvoří výčet tokenů ParamDef představujících parametry metody, na kterou odkazuje zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="be19d-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be19d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be19d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be19d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be19d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="be19d-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="be19d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="be19d-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="be19d-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="be19d-108">pro Token MethodDef reprezentující metodu s parametry pro výčet.</span><span class="sxs-lookup"><span data-stu-id="be19d-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="be19d-109">mimo Pole, které se používá k uložení tokenů ParamDef.</span><span class="sxs-lookup"><span data-stu-id="be19d-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="be19d-110">pro Maximální velikost `rParams` pole</span><span class="sxs-lookup"><span data-stu-id="be19d-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="be19d-111">mimo Počet tokenů ParamDef vrácených v `rParams`.</span><span class="sxs-lookup"><span data-stu-id="be19d-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be19d-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="be19d-112">Return Value</span></span>  
  
|<span data-ttu-id="be19d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be19d-113">HRESULT</span></span>|<span data-ttu-id="be19d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="be19d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="be19d-115">`EnumParams` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="be19d-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="be19d-116">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="be19d-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="be19d-117">V takovém případě je `pcTokens` nula.</span><span class="sxs-lookup"><span data-stu-id="be19d-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be19d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be19d-118">Requirements</span></span>  
 <span data-ttu-id="be19d-119">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be19d-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be19d-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be19d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be19d-121">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="be19d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be19d-122">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be19d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be19d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be19d-123">See also</span></span>

- [<span data-ttu-id="be19d-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be19d-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="be19d-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be19d-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
