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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ed9bae4fde96f0878e40ed73b81cc8776571ada5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468055"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="ee2c2-102">IMetaDataImport::GetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ee2c2-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="ee2c2-103">Získá metadata hodnot pro parametr odkazuje zadaný ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee2c2-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="ee2c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee2c2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ee2c2-106">[in] ParamDef token, který představuje parametr a vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="ee2c2-107">[out] Ukazatel na token MethodDef představující metodu, která přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="ee2c2-108">[out] Pořadové číslo pozice parametru v seznamu argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="ee2c2-109">[out] Vyrovnávací paměti, která bude uchovávat název parametru.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ee2c2-110">[in] Požadovaná velikost v širokých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ee2c2-111">[out] Velikost vrácené v širokých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ee2c2-112">[out] Ukazatel na libovolný atribut příznaky spojené s parametrem.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="ee2c2-113">To je bitová maska z `CorParamAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ee2c2-114">[out] Ukazatel na příznak určující, který je parametr <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ee2c2-115">[out] Ukazatel na konstantní řetězec vrácený funkcí parametru.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ee2c2-116">[out] Velikost `ppValue` v široké znaky, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee2c2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee2c2-117">Remarks</span></span>

<span data-ttu-id="ee2c2-118">Pořadí hodnot v `pulSequence` začínají znakem 1 pro parametry.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="ee2c2-119">Návratová hodnota má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="ee2c2-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee2c2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee2c2-120">Requirements</span></span>  
 <span data-ttu-id="ee2c2-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2c2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2c2-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee2c2-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee2c2-123">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee2c2-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee2c2-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2c2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2c2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee2c2-125">See also</span></span>
- [<span data-ttu-id="ee2c2-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee2c2-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ee2c2-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee2c2-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
