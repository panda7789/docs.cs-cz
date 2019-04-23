---
title: ICorDebugModule::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c28182feff8e4b7d49b7d068da1496d44fa2f917
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150355"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="10758-102">ICorDebugModule::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="10758-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="10758-103">Získá token pro záznam tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="10758-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10758-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10758-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10758-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10758-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="10758-106">[out] Ukazatel `mdModule` token, který odkazuje na metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="10758-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10758-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10758-107">Remarks</span></span>  
 <span data-ttu-id="10758-108">Token, který lze předat [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [imetadataimport2 –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), a [imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="10758-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10758-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10758-109">Requirements</span></span>  
 <span data-ttu-id="10758-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10758-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10758-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10758-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10758-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10758-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10758-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10758-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10758-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10758-114">See also</span></span>

- [<span data-ttu-id="10758-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="10758-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
