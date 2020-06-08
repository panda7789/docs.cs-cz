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
ms.openlocfilehash: a031cdb875b5eb046428d4d235d3093caddb7a6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491287"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="24290-102">IMetaDataImport::GetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="24290-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="24290-103">Získá ukazatel na nativní nespravovaný typ pole reprezentovaného tokenem metadat zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="24290-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24290-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24290-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24290-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24290-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="24290-106">pro Token metadat, který představuje pole pro získání informací o interop marshaling.</span><span class="sxs-lookup"><span data-stu-id="24290-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="24290-107">mimo Ukazatel na signaturu metadat pro nativní typ pole.</span><span class="sxs-lookup"><span data-stu-id="24290-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="24290-108">mimo Velikost v bajtech `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="24290-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24290-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24290-109">Requirements</span></span>  
 <span data-ttu-id="24290-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24290-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24290-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="24290-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24290-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="24290-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24290-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24290-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24290-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24290-114">See also</span></span>

- [<span data-ttu-id="24290-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24290-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="24290-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24290-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
