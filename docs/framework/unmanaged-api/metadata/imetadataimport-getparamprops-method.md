---
title: IMetaDataImport::GetParamProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: c2abf2813c6e1a9db4264bded32d9cb9c58a2bcb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491053"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="dfc92-102">IMetaDataImport::GetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="dfc92-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="dfc92-103">Načte hodnoty metadat pro parametr, na který odkazuje zadaný ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="dfc92-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfc92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfc92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfc92-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dfc92-106">pro Token ParamDef, který představuje parametr pro vrácení metadat.</span><span class="sxs-lookup"><span data-stu-id="dfc92-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="dfc92-107">mimo Ukazatel na token MethodDef představující metodu, která přijímá parametr.</span><span class="sxs-lookup"><span data-stu-id="dfc92-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="dfc92-108">mimo Pořadové místo parametru v seznamu argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="dfc92-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="dfc92-109">mimo Vyrovnávací paměť pro uložení názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="dfc92-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="dfc92-110">pro Požadovaná velikost v různých znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="dfc92-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="dfc92-111">mimo Vrácená velikost v různých znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="dfc92-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="dfc92-112">mimo Ukazatel na libovolný příznak atributu přidružený k parametru.</span><span class="sxs-lookup"><span data-stu-id="dfc92-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="dfc92-113">Toto je Bitová maska `CorParamAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="dfc92-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="dfc92-114">mimo Ukazatel na příznak určující, že parametr je <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="dfc92-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dfc92-115">mimo Ukazatel na konstantní řetězec vrácený parametrem.</span><span class="sxs-lookup"><span data-stu-id="dfc92-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="dfc92-116">mimo Velikost `ppValue` v rámci velkých znaků nebo nula, pokud `ppValue` řetězec nedrží.</span><span class="sxs-lookup"><span data-stu-id="dfc92-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfc92-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfc92-117">Remarks</span></span>

<span data-ttu-id="dfc92-118">Hodnoty sekvence začínají na `pulSequence` 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="dfc92-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="dfc92-119">Návratová hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="dfc92-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="dfc92-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfc92-120">Requirements</span></span>  
 <span data-ttu-id="dfc92-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc92-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc92-122">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dfc92-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfc92-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dfc92-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc92-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc92-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc92-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfc92-125">See also</span></span>

- [<span data-ttu-id="dfc92-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfc92-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dfc92-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfc92-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
