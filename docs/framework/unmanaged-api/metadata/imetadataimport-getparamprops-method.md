---
title: "IMetaDataImport::GetParamProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="378b1-102">IMetaDataImport::GetParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="378b1-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="378b1-103">Získá metadata hodnoty pro parametr odkazuje zadaný ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="378b1-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="378b1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="378b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="378b1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="378b1-106">[v] ParamDef token, který představuje parametr vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="378b1-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="378b1-107">[out] Ukazatel na MethodDef token představující metodu, která přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="378b1-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="378b1-108">[out] Pořadové číslo pozice parametr v seznamu argumentů metoda.</span><span class="sxs-lookup"><span data-stu-id="378b1-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="378b1-109">[out] Vyrovnávací paměť pro název parametru.</span><span class="sxs-lookup"><span data-stu-id="378b1-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="378b1-110">[v] Požadovaná velikost v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="378b1-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="378b1-111">[out] Vrácený velikost v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="378b1-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="378b1-112">[out] Ukazatel na žádné příznaky atribut spojené s parametrem.</span><span class="sxs-lookup"><span data-stu-id="378b1-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="378b1-113">[out] Ukazatel na příznak určující, který je parametr <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="378b1-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="378b1-114">[out] Ukazatel na konstantní řetězec vrácený parametr.</span><span class="sxs-lookup"><span data-stu-id="378b1-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="378b1-115">[out] Velikost `ppValue` v široké znaky, nebo nula, pokud `ppValue` neobsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="378b1-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378b1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="378b1-116">Requirements</span></span>  
 <span data-ttu-id="378b1-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378b1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378b1-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="378b1-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="378b1-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="378b1-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="378b1-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378b1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378b1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="378b1-121">See Also</span></span>  
 [<span data-ttu-id="378b1-122">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="378b1-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="378b1-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="378b1-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
