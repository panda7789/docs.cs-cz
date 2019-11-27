---
title: IMetaDataImport::GetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: c9ac624e17223def206e86fd92ee4fd2de7f6082
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436745"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="807be-102">IMetaDataImport::GetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="807be-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="807be-103">Vrátí informace o metadatech pro <xref:System.Type> reprezentované zadaným tokenem TypeDef.</span><span class="sxs-lookup"><span data-stu-id="807be-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="807be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="807be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="807be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="807be-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="807be-106">pro Token TypeDef, který představuje typ, pro který se mají vracet metadata.</span><span class="sxs-lookup"><span data-stu-id="807be-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="807be-107">mimo Vyrovnávací paměť obsahující název typu.</span><span class="sxs-lookup"><span data-stu-id="807be-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="807be-108">pro Velikost v různých znacích `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="807be-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="807be-109">mimo Počet velkých znaků vrácených v `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="807be-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="807be-110">mimo Ukazatel na libovolný příznak, který upraví definici typu.</span><span class="sxs-lookup"><span data-stu-id="807be-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="807be-111">Tato hodnota je Bitová maska z výčtu [CorTypeAttr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="807be-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="807be-112">mimo Token metadat TypeDef nebo TypeRef, který představuje základní typ požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="807be-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="807be-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="807be-113">Requirements</span></span>  
 <span data-ttu-id="807be-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="807be-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="807be-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="807be-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="807be-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="807be-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="807be-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="807be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807be-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="807be-118">See also</span></span>

- [<span data-ttu-id="807be-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="807be-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="807be-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="807be-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
