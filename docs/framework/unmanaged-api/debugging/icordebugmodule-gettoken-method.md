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
ms.openlocfilehash: a6aff37a480460bfed7064d59b4c5276daf3207c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212498"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="993ff-102">ICorDebugModule::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="993ff-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="993ff-103">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="993ff-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="993ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="993ff-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="993ff-106">mimo Ukazatel na `mdModule` token, který odkazuje na metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="993ff-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="993ff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="993ff-107">Remarks</span></span>  
 <span data-ttu-id="993ff-108">Token se dá předat rozhraním pro import metadat [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)a [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="993ff-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993ff-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="993ff-109">Requirements</span></span>  
 <span data-ttu-id="993ff-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993ff-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="993ff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="993ff-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="993ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="993ff-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993ff-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="993ff-114">See also</span></span>

- [<span data-ttu-id="993ff-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="993ff-115">Metadata</span></span>](../metadata/index.md)
