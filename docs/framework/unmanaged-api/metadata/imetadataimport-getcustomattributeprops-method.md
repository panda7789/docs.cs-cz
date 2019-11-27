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
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437645"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="c8425-102">IMetaDataImport::GetCustomAttributeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c8425-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="c8425-103">Získá hodnotu vlastního atributu s ohledem na jeho token metadat.</span><span class="sxs-lookup"><span data-stu-id="c8425-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8425-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8425-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8425-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8425-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="c8425-106">pro Token metadat, který představuje vlastní atribut, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="c8425-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="c8425-107">[out, volitelné] Token metadat představující objekt, který upravuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="c8425-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="c8425-108">Tato hodnota může být jakýkoli typ tokenu metadat s výjimkou `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="c8425-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="c8425-109">[out, volitelné] Token metadat `mdMethodDef` nebo `mdMemberRef` reprezentující <xref:System.Type> vráceného vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="c8425-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="c8425-110">[out, volitelné] Ukazatel na pole dat, které je hodnotou vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="c8425-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c8425-111">[out, volitelné] Velikost v bajtech dat vrácených ve formátu \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="c8425-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8425-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8425-112">Remarks</span></span>  
 <span data-ttu-id="c8425-113">Vlastní atribut je uložen jako pole dat, formátu srozumitelného modulem metadat.</span><span class="sxs-lookup"><span data-stu-id="c8425-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8425-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8425-114">Requirements</span></span>  
 <span data-ttu-id="c8425-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8425-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8425-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c8425-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8425-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8425-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8425-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8425-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8425-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8425-119">See also</span></span>

- [<span data-ttu-id="c8425-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8425-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c8425-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8425-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
