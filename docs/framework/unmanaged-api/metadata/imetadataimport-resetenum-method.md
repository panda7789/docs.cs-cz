---
title: IMetaDataImport::ResetEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: bc7f1740d666211b63cd93e6f1c0e6955f61ec5d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503455"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="1424b-102">IMetaDataImport::ResetEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="1424b-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="1424b-103">Obnoví zadaný enumerátor na určenou pozici.</span><span class="sxs-lookup"><span data-stu-id="1424b-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1424b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1424b-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1424b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1424b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="1424b-106">pro Enumerátor, který má být resetován.</span><span class="sxs-lookup"><span data-stu-id="1424b-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="1424b-107">pro Nová pozice, na kterou chcete umístit enumerátor.</span><span class="sxs-lookup"><span data-stu-id="1424b-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1424b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1424b-108">Requirements</span></span>  
 <span data-ttu-id="1424b-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1424b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1424b-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1424b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1424b-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1424b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1424b-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1424b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1424b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1424b-113">See also</span></span>

- [<span data-ttu-id="1424b-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1424b-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1424b-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1424b-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
