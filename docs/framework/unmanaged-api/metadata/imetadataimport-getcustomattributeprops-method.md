---
title: IMetaDataImport::GetCustomAttributeProps – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4619d5a1444d42c6f3ac43306fbd979a6a70f12b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672172"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="3ab33-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="3ab33-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="3ab33-103">Získá hodnotu vlastní atribut zadaný svůj token metadat.</span><span class="sxs-lookup"><span data-stu-id="3ab33-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ab33-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ab33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ab33-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="3ab33-106">[in] Token metadat, který představuje vlastní atribut, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="3ab33-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="3ab33-107">[out, volitelné] Token metadat představující objekt, který upravuje vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="3ab33-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="3ab33-108">Tato hodnota může být libovolný typ tokenu metadat s výjimkou `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="3ab33-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="3ab33-109">[out, volitelné] `mdMethodDef` Nebo `mdMemberRef` představující token metadat <xref:System.Type> vrácené vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="3ab33-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="3ab33-110">[out, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="3ab33-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="3ab33-111">[out, volitelné] Velikost v bajtech dat vrácených v \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="3ab33-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ab33-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ab33-112">Remarks</span></span>  
 <span data-ttu-id="3ab33-113">Vlastní atribut je uložena jako pole dat, formát, který je srozumitelné pro modul metadat.</span><span class="sxs-lookup"><span data-stu-id="3ab33-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab33-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ab33-114">Requirements</span></span>  
 <span data-ttu-id="3ab33-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ab33-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab33-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ab33-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ab33-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ab33-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ab33-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ab33-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab33-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ab33-119">See also</span></span>
- [<span data-ttu-id="3ab33-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ab33-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3ab33-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ab33-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
