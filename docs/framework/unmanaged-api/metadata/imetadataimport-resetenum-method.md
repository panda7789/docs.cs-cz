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
ms.openlocfilehash: 3dd82588cf2dbf92fdda66fd7674c17ddc8b7306
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177193"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="d9e44-102">IMetaDataImport::ResetEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="d9e44-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="d9e44-103">Obnoví zadaný čítač výčtu na zadanou pozici.</span><span class="sxs-lookup"><span data-stu-id="d9e44-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e44-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9e44-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d9e44-106">[v] Čítač výčtu resetovat.</span><span class="sxs-lookup"><span data-stu-id="d9e44-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="d9e44-107">[v] Nové pozice, na které chcete umístit čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="d9e44-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e44-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9e44-108">Requirements</span></span>  
 <span data-ttu-id="d9e44-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e44-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e44-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d9e44-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9e44-111">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9e44-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e44-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e44-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e44-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9e44-113">See also</span></span>

- [<span data-ttu-id="d9e44-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9e44-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d9e44-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9e44-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
