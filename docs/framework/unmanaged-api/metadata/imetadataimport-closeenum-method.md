---
title: IMetaDataImport::CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492473"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="a5645-102">IMetaDataImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="a5645-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="a5645-103">Ukončí enumerátor, který je identifikován specifikovaným popisovačem.</span><span class="sxs-lookup"><span data-stu-id="a5645-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5645-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5645-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5645-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5645-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a5645-106">pro Popisovač pro zavření čítače.</span><span class="sxs-lookup"><span data-stu-id="a5645-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5645-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5645-107">Remarks</span></span>  
 <span data-ttu-id="a5645-108">Popisovač určený pomocí `hEnum` je získán z předchozího `Enum` *názvu* volání (například [IMetaDataImport:: enumtypedefs –](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="a5645-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5645-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5645-109">Requirements</span></span>  
 <span data-ttu-id="a5645-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5645-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5645-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a5645-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5645-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5645-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5645-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5645-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5645-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5645-114">See also</span></span>

- [<span data-ttu-id="a5645-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5645-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a5645-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5645-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
