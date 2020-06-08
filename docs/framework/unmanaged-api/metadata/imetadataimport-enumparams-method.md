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
ms.openlocfilehash: f9a58a70b5264d7f1eb33fb0e09c702c94a13e85
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491753"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="8dc92-102">IMetaDataImport::EnumParams – metoda</span><span class="sxs-lookup"><span data-stu-id="8dc92-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="8dc92-103">Vytvoří výčet tokenů ParamDef představujících parametry metody, na kterou odkazuje zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="8dc92-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dc92-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dc92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8dc92-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8dc92-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="8dc92-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8dc92-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="8dc92-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="8dc92-108">pro Token MethodDef reprezentující metodu s parametry pro výčet.</span><span class="sxs-lookup"><span data-stu-id="8dc92-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="8dc92-109">mimo Pole, které se používá k uložení tokenů ParamDef.</span><span class="sxs-lookup"><span data-stu-id="8dc92-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8dc92-110">pro Maximální velikost `rParams` pole.</span><span class="sxs-lookup"><span data-stu-id="8dc92-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8dc92-111">mimo Počet vrácených tokenů ParamDef `rParams` .</span><span class="sxs-lookup"><span data-stu-id="8dc92-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dc92-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8dc92-112">Return Value</span></span>  
  
|<span data-ttu-id="8dc92-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8dc92-113">HRESULT</span></span>|<span data-ttu-id="8dc92-114">Description</span><span class="sxs-lookup"><span data-stu-id="8dc92-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8dc92-115">`EnumParams`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8dc92-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8dc92-116">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="8dc92-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="8dc92-117">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="8dc92-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8dc92-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8dc92-118">Requirements</span></span>  
 <span data-ttu-id="8dc92-119">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dc92-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dc92-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8dc92-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dc92-121">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="8dc92-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8dc92-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dc92-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc92-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dc92-123">See also</span></span>

- [<span data-ttu-id="8dc92-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dc92-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8dc92-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8dc92-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
