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
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501882"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="8c012-102">ICorDebugModule::GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="8c012-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="8c012-103">Získá token pro položku tabulky pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="8c012-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c012-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c012-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c012-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c012-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="8c012-106">mimo Ukazatel na `mdModule` token, který odkazuje na metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="8c012-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c012-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c012-107">Remarks</span></span>  
 <span data-ttu-id="8c012-108">Token se dá předat rozhraním pro import metadat [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md)a [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8c012-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c012-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c012-109">Requirements</span></span>  
 <span data-ttu-id="8c012-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c012-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c012-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c012-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c012-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c012-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c012-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c012-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c012-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c012-114">See also</span></span>

- [<span data-ttu-id="8c012-115">Metadata</span><span class="sxs-lookup"><span data-stu-id="8c012-115">Metadata</span></span>](../metadata/index.md)
