---
title: IMetaDataImport::GetCustomAttributeProps – metoda
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
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
caps.latest.revision: 14
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1e6ef9443b99b3e6b36154558ce226d421dbc0a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="ab0e6-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ab0e6-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="ab0e6-103">Získá hodnotu atributu vlastní zadaný token jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab0e6-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab0e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab0e6-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="ab0e6-106">[v] Metadata token, který představuje vlastní atribut mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="ab0e6-107">[na víc systémů, volitelné] Metadata token představující objektu, která upraví vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="ab0e6-108">Tato hodnota může být jakýkoli typ metadat token s výjimkou `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="ab0e6-109">[na víc systémů, volitelné] `mdMethodDef` Nebo `mdMemberRef` metadata token reprezentující <xref:System.Type> vrácený vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="ab0e6-110">[na víc systémů, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="ab0e6-111">[na víc systémů, volitelné] Velikost v bajtech data v \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab0e6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab0e6-112">Remarks</span></span>  
 <span data-ttu-id="ab0e6-113">Vlastní atribut se ukládají jako pole dat, formátu, který se rozumí modul metadat.</span><span class="sxs-lookup"><span data-stu-id="ab0e6-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0e6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab0e6-114">Requirements</span></span>  
 <span data-ttu-id="ab0e6-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0e6-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab0e6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab0e6-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab0e6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab0e6-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0e6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab0e6-119">See Also</span></span>  
 [<span data-ttu-id="ab0e6-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab0e6-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ab0e6-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab0e6-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
