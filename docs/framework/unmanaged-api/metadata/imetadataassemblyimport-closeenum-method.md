---
title: IMetaDataAssemblyImport::CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c5477578491c3cbc3f5fce694820971e99b45079
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444097"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="f4612-102">IMetaDataAssemblyImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="f4612-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="f4612-103">Uvolní odkaz na instanci zadaný výčet.</span><span class="sxs-lookup"><span data-stu-id="f4612-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4612-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4612-104">Syntax</span></span>  
  
```  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4612-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4612-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f4612-106">[v] Výčet instance bude uzavřen.</span><span class="sxs-lookup"><span data-stu-id="f4612-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4612-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4612-107">Requirements</span></span>  
 <span data-ttu-id="f4612-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4612-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4612-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4612-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4612-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4612-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4612-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4612-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4612-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4612-112">See Also</span></span>  
 [<span data-ttu-id="f4612-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4612-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
