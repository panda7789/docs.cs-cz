---
title: "ICorDebugModule::GetToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 651612b07a69f0cbcc9c818fe7627bf496f6d68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="df453-102">ICorDebugModule::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="df453-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="df453-103">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="df453-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df453-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df453-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df453-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df453-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="df453-106">[out] Ukazatel `mdModule` token, který odkazuje na metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="df453-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df453-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df453-107">Remarks</span></span>  
 <span data-ttu-id="df453-108">Token se dá předat do [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [imetadataimport2 –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), a [imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní import metadat.</span><span class="sxs-lookup"><span data-stu-id="df453-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df453-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df453-109">Requirements</span></span>  
 <span data-ttu-id="df453-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df453-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df453-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df453-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df453-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df453-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df453-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df453-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df453-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="df453-114">See Also</span></span>  
 [<span data-ttu-id="df453-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="df453-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
