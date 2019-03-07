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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab5200cbd3a37bba31d52f9934e11aecc88c59c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502407"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="53d67-102">IMetaDataImport::EnumParams – metoda</span><span class="sxs-lookup"><span data-stu-id="53d67-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="53d67-103">Vytvoří výčet ParamDef tokeny představující parametry metody odkazuje zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="53d67-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53d67-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53d67-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="53d67-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="53d67-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="53d67-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="53d67-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="53d67-108">[in] Token MethodDef představující metodu s parametry pro vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="53d67-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="53d67-109">[out] Pole pro ukládání tokenů ParamDef.</span><span class="sxs-lookup"><span data-stu-id="53d67-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="53d67-110">[in] Maximální velikost `rParams` pole.</span><span class="sxs-lookup"><span data-stu-id="53d67-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="53d67-111">[out] Počet tokenů ParamDef vrácené v `rParams`.</span><span class="sxs-lookup"><span data-stu-id="53d67-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53d67-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="53d67-112">Return Value</span></span>  
  
|<span data-ttu-id="53d67-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53d67-113">HRESULT</span></span>|<span data-ttu-id="53d67-114">Popis</span><span class="sxs-lookup"><span data-stu-id="53d67-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="53d67-115">`EnumParams` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="53d67-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="53d67-116">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="53d67-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="53d67-117">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="53d67-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53d67-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53d67-118">Requirements</span></span>  
 <span data-ttu-id="53d67-119">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53d67-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d67-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53d67-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53d67-121">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53d67-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53d67-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53d67-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d67-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53d67-123">See also</span></span>
- [<span data-ttu-id="53d67-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53d67-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="53d67-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53d67-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
