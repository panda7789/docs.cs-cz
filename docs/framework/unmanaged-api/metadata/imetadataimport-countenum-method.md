---
title: IMetaDataImport::CountEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177359"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="99de2-102">IMetaDataImport::CountEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="99de2-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="99de2-103">Získá počet prvků ve výčtu, který byl načten zadaným čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="99de2-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99de2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99de2-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99de2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99de2-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="99de2-106">[v] Popisovač pro čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="99de2-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="99de2-107">[out] Počet prvků ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="99de2-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99de2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99de2-108">Remarks</span></span>  
 <span data-ttu-id="99de2-109">Popisovač zadaný `hEnum` podle je `Enum`získán z *předchozího* name volání (například [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="99de2-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99de2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99de2-110">Requirements</span></span>  
 <span data-ttu-id="99de2-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99de2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99de2-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="99de2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99de2-113">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99de2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99de2-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99de2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99de2-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="99de2-115">See also</span></span>

- [<span data-ttu-id="99de2-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99de2-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="99de2-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99de2-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
