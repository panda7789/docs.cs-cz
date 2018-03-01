---
title: "IMetaDataImport::GetCustomAttributeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1e6ef9443b99b3e6b36154558ce226d421dbc0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="b7b28-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b7b28-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="b7b28-103">Získá hodnotu atributu vlastní zadaný token jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="b7b28-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7b28-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7b28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7b28-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="b7b28-106">[v] Metadata token, který představuje vlastní atribut mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="b7b28-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="b7b28-107">[na víc systémů, volitelné] Metadata token představující objektu, která upraví vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="b7b28-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="b7b28-108">Tato hodnota může být jakýkoli typ metadat token s výjimkou `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="b7b28-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="b7b28-109">[na víc systémů, volitelné] `mdMethodDef` Nebo `mdMemberRef` metadata token reprezentující <xref:System.Type> vrácený vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b7b28-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="b7b28-110">[na víc systémů, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b7b28-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="b7b28-111">[na víc systémů, volitelné] Velikost v bajtech data v \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="b7b28-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7b28-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7b28-112">Remarks</span></span>  
 <span data-ttu-id="b7b28-113">Vlastní atribut se ukládají jako pole dat, formátu, který se rozumí modul metadat.</span><span class="sxs-lookup"><span data-stu-id="b7b28-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b28-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7b28-114">Requirements</span></span>  
 <span data-ttu-id="b7b28-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b28-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b28-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7b28-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7b28-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7b28-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7b28-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b28-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b28-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7b28-119">See Also</span></span>  
 [<span data-ttu-id="b7b28-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7b28-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b7b28-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7b28-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
