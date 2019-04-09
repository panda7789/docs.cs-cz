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
ms.openlocfilehash: c27a55166ebc055f324ec45ba6dfd835c8b8bbf6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075740"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="a7129-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a7129-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="a7129-103">Získá hodnotu vlastní atribut zadaný svůj token metadat.</span><span class="sxs-lookup"><span data-stu-id="a7129-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7129-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7129-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7129-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7129-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="a7129-106">[in] Token metadat, který představuje vlastní atribut, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="a7129-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="a7129-107">[out, volitelné] Token metadat představující objekt, který upravuje vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="a7129-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="a7129-108">Tato hodnota může být libovolný typ tokenu metadat s výjimkou `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a7129-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="a7129-109">[out, volitelné] `mdMethodDef` Nebo `mdMemberRef` představující token metadat <xref:System.Type> vrácené vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="a7129-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="a7129-110">[out, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="a7129-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="a7129-111">[out, volitelné] Velikost v bajtech dat vrácených v \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="a7129-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7129-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7129-112">Remarks</span></span>  
 <span data-ttu-id="a7129-113">Vlastní atribut je uložena jako pole dat, formát, který je srozumitelné pro modul metadat.</span><span class="sxs-lookup"><span data-stu-id="a7129-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7129-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7129-114">Requirements</span></span>  
 <span data-ttu-id="a7129-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7129-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7129-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7129-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7129-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7129-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a7129-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a7129-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7129-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7129-119">See also</span></span>

- [<span data-ttu-id="a7129-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7129-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a7129-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7129-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
