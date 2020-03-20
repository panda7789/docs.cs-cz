---
title: IMetaDataImport::GetFieldMarshal – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: 91a19e5e15dddd446208dfa3b2c32826282067eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175392"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="1db52-102">IMetaDataImport::GetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="1db52-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="1db52-103">Získá ukazatel na nativní, nespravovaný typ pole reprezentované tokenem metadat zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="1db52-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1db52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1db52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1db52-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1db52-106">[v] Token metadat, který představuje pole získat interop zařazování informace.</span><span class="sxs-lookup"><span data-stu-id="1db52-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="1db52-107">[out] Ukazatel na podpis metadat nativního typu pole.</span><span class="sxs-lookup"><span data-stu-id="1db52-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="1db52-108">[out] Velikost v bajtů `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="1db52-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db52-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1db52-109">Requirements</span></span>  
 <span data-ttu-id="1db52-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1db52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db52-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1db52-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1db52-112">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1db52-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1db52-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db52-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db52-114">See also</span></span>

- [<span data-ttu-id="1db52-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1db52-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1db52-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1db52-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
