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
ms.openlocfilehash: 683c2853ea2ed43e61eb666ec56619cb58cde273
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129500"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="5e1d7-102">ICorDebugModule::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="5e1d7-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="5e1d7-103">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="5e1d7-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e1d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e1d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e1d7-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="5e1d7-106">mimo Ukazatel na token `mdModule`, který odkazuje na metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="5e1d7-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e1d7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e1d7-107">Remarks</span></span>  
 <span data-ttu-id="5e1d7-108">Token se dá předat rozhraním pro import metadat [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)a [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5e1d7-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e1d7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e1d7-109">Requirements</span></span>  
 <span data-ttu-id="5e1d7-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1d7-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e1d7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e1d7-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e1d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e1d7-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1d7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e1d7-114">See also</span></span>

- [<span data-ttu-id="5e1d7-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="5e1d7-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
