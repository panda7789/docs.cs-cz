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
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492379"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="40594-102">IMetaDataImport::CountEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="40594-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="40594-103">Získá počet prvků ve výčtu, který byl načten zadaným výčtem.</span><span class="sxs-lookup"><span data-stu-id="40594-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40594-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40594-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40594-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40594-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="40594-106">pro Popisovač pro enumerátor.</span><span class="sxs-lookup"><span data-stu-id="40594-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="40594-107">mimo Počet prvků výčtu.</span><span class="sxs-lookup"><span data-stu-id="40594-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40594-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40594-108">Remarks</span></span>  
 <span data-ttu-id="40594-109">Popisovač určený pomocí `hEnum` je získán z předchozího `Enum` *názvu* volání (například [IMetaDataImport:: enumtypedefs –](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="40594-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40594-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40594-110">Requirements</span></span>  
 <span data-ttu-id="40594-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40594-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40594-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="40594-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40594-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40594-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40594-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40594-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40594-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40594-115">See also</span></span>

- [<span data-ttu-id="40594-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40594-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="40594-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40594-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
