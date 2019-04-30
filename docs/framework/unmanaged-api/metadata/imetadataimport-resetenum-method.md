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
ms.openlocfilehash: 143b11f0a99081b7d49bfbb68b635d92cf1e9ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777426"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="a259c-102">IMetaDataImport::ResetEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="a259c-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="a259c-103">Zadaný čítač resetuje na určenou pozici.</span><span class="sxs-lookup"><span data-stu-id="a259c-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a259c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a259c-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a259c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a259c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a259c-106">[in] Enumerátor resetovat.</span><span class="sxs-lookup"><span data-stu-id="a259c-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="a259c-107">[in] Nové umístění, kam chcete umístit enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a259c-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a259c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a259c-108">Requirements</span></span>  
 <span data-ttu-id="a259c-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a259c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a259c-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a259c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a259c-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a259c-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a259c-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a259c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a259c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a259c-113">See also</span></span>

- [<span data-ttu-id="a259c-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a259c-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a259c-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a259c-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
