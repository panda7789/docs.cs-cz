---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48249bb634c301b7fda2c360c3b793e9206a759a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737899"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="b6ad1-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="b6ad1-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="b6ad1-103">Získá modul, který odpovídá rozhraní daná metadata.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ad1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ad1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6ad1-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="b6ad1-106">[in] Ukazatel na objekt, který je součástí [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="b6ad1-107">[out] Ukazatel na adresu icordebugmodule – objekt, který představuje modul odpovídající rozhraní daná metadata.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ad1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6ad1-108">Requirements</span></span>  
 <span data-ttu-id="b6ad1-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ad1-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6ad1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6ad1-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ad1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ad1-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ad1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
