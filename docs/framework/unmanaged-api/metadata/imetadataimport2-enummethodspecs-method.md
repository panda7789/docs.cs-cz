---
title: IMetaDataImport2::EnumMethodSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177177"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="423e4-102">IMetaDataImport2::EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="423e4-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="423e4-103">Získá čítač pro pole MethodSpec tokeny přidružené k zadané MethodDef nebo MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="423e4-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="423e4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="423e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="423e4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="423e4-106">[dovnitř, ven] Ukazatel na čítač `rMethodSpecs`výčtu pro .</span><span class="sxs-lookup"><span data-stu-id="423e4-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="423e4-107">[v] Token MemberRef nebo MethodDef, který představuje metodu, jejíž tokeny MethodSpec mají být uvedeny ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="423e4-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="423e4-108">Pokud `tk` je hodnota 0 (nula), budou uvedeny všechny tokeny MethodSpec v oboru.</span><span class="sxs-lookup"><span data-stu-id="423e4-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="423e4-109">[out] Pole MethodSpec tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="423e4-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="423e4-110">[v] Požadovaný maximální počet tokenů, `rMethodSpecs`které mají být umístit v .</span><span class="sxs-lookup"><span data-stu-id="423e4-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="423e4-111">[out] Vrácený počet tokenů `rMethodSpecs`umístěných v .</span><span class="sxs-lookup"><span data-stu-id="423e4-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="423e4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="423e4-112">Return Value</span></span>  
  
|<span data-ttu-id="423e4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="423e4-113">HRESULT</span></span>|<span data-ttu-id="423e4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="423e4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="423e4-115">`EnumMethodSpecs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="423e4-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="423e4-116">`phEnum`nemá žádné členské prvky.</span><span class="sxs-lookup"><span data-stu-id="423e4-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="423e4-117">V tomto `pcMethodSpecs` případě je nastavena na 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="423e4-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="423e4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="423e4-118">Requirements</span></span>  
 <span data-ttu-id="423e4-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="423e4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="423e4-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="423e4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="423e4-121">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="423e4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="423e4-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="423e4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423e4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="423e4-123">See also</span></span>

- [<span data-ttu-id="423e4-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="423e4-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="423e4-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="423e4-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
