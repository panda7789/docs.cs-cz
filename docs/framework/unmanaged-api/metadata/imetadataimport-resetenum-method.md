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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa5a446ba7bfd70330601c7cbc129800761cdb7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782623"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="04f6e-102">IMetaDataImport::ResetEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="04f6e-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="04f6e-103">Zadaný čítač resetuje na určenou pozici.</span><span class="sxs-lookup"><span data-stu-id="04f6e-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04f6e-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04f6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04f6e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="04f6e-106">[in] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="04f6e-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="04f6e-107">[in] Nové umístění, kam chcete umístit enumerátor.</span><span class="sxs-lookup"><span data-stu-id="04f6e-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f6e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04f6e-108">Requirements</span></span>  
 <span data-ttu-id="04f6e-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f6e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f6e-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04f6e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04f6e-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04f6e-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04f6e-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f6e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f6e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04f6e-113">See also</span></span>

- [<span data-ttu-id="04f6e-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04f6e-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="04f6e-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04f6e-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
