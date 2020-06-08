---
title: IMetaDataEmit2::DefineGenericParam – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: e4401ea8a70e7ace8d8efc5e0a6d29f6db51b3df
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503806"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="372a3-102">IMetaDataEmit2::DefineGenericParam – metoda</span><span class="sxs-lookup"><span data-stu-id="372a3-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="372a3-103">Vytvoří definici pro parametr obecného typu a získá token k tomuto parametru obecného typu.</span><span class="sxs-lookup"><span data-stu-id="372a3-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="372a3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="372a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="372a3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="372a3-106">pro `mdTypeDef`Token nebo `mdMethodDef` , který představuje metodu nebo konstruktor, pro který chcete definovat obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="372a3-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="372a3-107">pro Index obecného parametru</span><span class="sxs-lookup"><span data-stu-id="372a3-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="372a3-108">pro Hodnota výčtu [CorGenericParamAttr –](corgenericparamattr-enumeration.md) , která popisuje typ obecného parametru.</span><span class="sxs-lookup"><span data-stu-id="372a3-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="372a3-109">pro Název parametru</span><span class="sxs-lookup"><span data-stu-id="372a3-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="372a3-110">pro Tento parametr je vyhrazen pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="372a3-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="372a3-111">pro Pole s nulovým zakončením v poli omezení typu.</span><span class="sxs-lookup"><span data-stu-id="372a3-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="372a3-112">Členy pole musí být `mdTypeDef` `mdTypeRef` token metadat, nebo `mdTypeSpec` .</span><span class="sxs-lookup"><span data-stu-id="372a3-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="372a3-113">mimo Token, který představuje obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="372a3-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="372a3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="372a3-114">Requirements</span></span>  
 <span data-ttu-id="372a3-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="372a3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="372a3-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="372a3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="372a3-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="372a3-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="372a3-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="372a3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372a3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="372a3-119">See also</span></span>

- [<span data-ttu-id="372a3-120">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="372a3-120">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="372a3-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="372a3-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
