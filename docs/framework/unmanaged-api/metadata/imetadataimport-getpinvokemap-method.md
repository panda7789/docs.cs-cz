---
title: "IMetaDataImport::GetPinvokeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: adb6a9a5f53dcfd8ada5b3aa9d75daac18d50283
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="ddafe-102">IMetaDataImport::GetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="ddafe-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="ddafe-103">Získá odkaz ModuleRef token představující cíl sestavení volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="ddafe-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddafe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddafe-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddafe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddafe-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ddafe-106">[v] Token FieldDef nebo MethodDef získat metadata PInvoke mapování.</span><span class="sxs-lookup"><span data-stu-id="ddafe-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="ddafe-107">[out] Ukazatel na příznaky použité pro mapování.</span><span class="sxs-lookup"><span data-stu-id="ddafe-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="ddafe-108">Tato hodnota je bitová maska z [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="ddafe-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="ddafe-109">[out] Název nespravované cílový DLL.</span><span class="sxs-lookup"><span data-stu-id="ddafe-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="ddafe-110">[v] Velikost v široké znaky `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="ddafe-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="ddafe-111">[out] Počet široké znaky, vrátí se v `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="ddafe-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="ddafe-112">[out] Ukazatel na odkaz ModuleRef token, který představuje nespravovaný cíl objektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="ddafe-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddafe-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddafe-113">Requirements</span></span>  
 <span data-ttu-id="ddafe-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddafe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddafe-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddafe-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddafe-116">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddafe-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddafe-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddafe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddafe-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddafe-118">See Also</span></span>  
 [<span data-ttu-id="ddafe-119">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddafe-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ddafe-120">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddafe-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
