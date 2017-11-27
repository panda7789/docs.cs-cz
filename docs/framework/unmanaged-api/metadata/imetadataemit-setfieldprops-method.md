---
title: "IMetaDataEmit::SetFieldProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f031e79deab57184043eaa44d2d8a3d369187c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="d1c67-102">IMetaDataEmit::SetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="d1c67-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="d1c67-103">Nastaví nebo aktualizuje výchozí hodnota pro pole odkazuje token zadané pole.</span><span class="sxs-lookup"><span data-stu-id="d1c67-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1c67-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1c67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1c67-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="d1c67-106">[v] Token pro cílové pole.</span><span class="sxs-lookup"><span data-stu-id="d1c67-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="d1c67-107">[v] Atributy pole.</span><span class="sxs-lookup"><span data-stu-id="d1c67-107">[in] Field attributes.</span></span> <span data-ttu-id="d1c67-108">Toto je bitová maska s `CorFieldAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d1c67-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="d1c67-109">[v] `ELEMENT_TYPE_`  *\**  Pro konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d1c67-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="d1c67-110">Toto je `CorElementType` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d1c67-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="d1c67-111">Pokud není definovaný konstanta, nastavte hodnotu `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="d1c67-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="d1c67-112">[v] Hodnota konstanty pro pole.</span><span class="sxs-lookup"><span data-stu-id="d1c67-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="d1c67-113">[v] Velikost v znaky Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="d1c67-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c67-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1c67-114">Requirements</span></span>  
 <span data-ttu-id="d1c67-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1c67-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1c67-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1c67-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1c67-117">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1c67-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1c67-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1c67-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c67-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1c67-119">See Also</span></span>  
 [<span data-ttu-id="d1c67-120">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1c67-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d1c67-121">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1c67-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
