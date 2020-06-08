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
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490715"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="16f0d-102">IMetaDataImport2::EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="16f0d-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="16f0d-103">Získá enumerátor pro pole tokenů MethodSpec přidružených k zadanému tokenu MethodDef nebo MemberRef.</span><span class="sxs-lookup"><span data-stu-id="16f0d-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16f0d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="16f0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16f0d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="16f0d-106">[in, out] Ukazatel na enumerátor pro `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="16f0d-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="16f0d-107">pro Token MemberRef nebo MethodDef, který představuje metodu, jejíž tokeny MethodSpec mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="16f0d-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="16f0d-108">Pokud `tk` je hodnota 0 (nula), vyčíslení všech tokenů MethodSpec v oboru bude vyhodnoceno.</span><span class="sxs-lookup"><span data-stu-id="16f0d-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="16f0d-109">mimo Pole tokenů MethodSpec k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="16f0d-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="16f0d-110">pro Požadovaný maximální počet tokenů pro umístění `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="16f0d-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="16f0d-111">mimo Vrácený počet tokenů, které jsou umístěny v `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="16f0d-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16f0d-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="16f0d-112">Return Value</span></span>  
  
|<span data-ttu-id="16f0d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16f0d-113">HRESULT</span></span>|<span data-ttu-id="16f0d-114">Description</span><span class="sxs-lookup"><span data-stu-id="16f0d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="16f0d-115">`EnumMethodSpecs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="16f0d-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="16f0d-116">`phEnum`neobsahuje žádné prvky členů.</span><span class="sxs-lookup"><span data-stu-id="16f0d-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="16f0d-117">V tomto případě `pcMethodSpecs` je nastaveno na hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="16f0d-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16f0d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16f0d-118">Requirements</span></span>  
 <span data-ttu-id="16f0d-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16f0d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16f0d-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="16f0d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16f0d-121">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="16f0d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16f0d-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16f0d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f0d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16f0d-123">See also</span></span>

- [<span data-ttu-id="16f0d-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f0d-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="16f0d-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16f0d-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
