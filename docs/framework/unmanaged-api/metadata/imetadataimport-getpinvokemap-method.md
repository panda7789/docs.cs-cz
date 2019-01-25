---
title: IMetaDataImport::GetPinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2aed3367e20e32a387c8a1c58ead2899fbf0dcb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521436"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="0e7e4-102">IMetaDataImport::GetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="0e7e4-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="0e7e4-103">Získá token představující cílové sestavení volání PInvoke Odkaz ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e7e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e7e4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0e7e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e7e4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0e7e4-106">[in] FieldDef nebo MethodDef token pro získání metadat PInvoke mapování.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="0e7e4-107">[out] Ukazatel na příznaky použité pro mapování.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="0e7e4-108">Tato hodnota je bitová maska z [corpinvokemap –](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="0e7e4-109">[out] Název nespravovanému cílovému knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="0e7e4-110">[in] Velikost v širokých znaků `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="0e7e4-111">[out] Počet širokých znaků, které jsou vráceny v `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="0e7e4-112">[out] Ukazatel na odkaz ModuleRef token, který představuje nespravovaný cíl objektu knihovny.</span><span class="sxs-lookup"><span data-stu-id="0e7e4-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e7e4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e7e4-113">Requirements</span></span>  
 <span data-ttu-id="0e7e4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e7e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e7e4-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e7e4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e7e4-116">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e7e4-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e7e4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e7e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e7e4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e7e4-118">See also</span></span>
- [<span data-ttu-id="0e7e4-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e7e4-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0e7e4-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e7e4-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
