---
title: ICorDebugModule::GetClassFromToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 195cea23313d88b636479147faa512889ca94b17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413969"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="12a83-102">ICorDebugModule::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="12a83-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="12a83-103">Získá třídu určeného token metadat.</span><span class="sxs-lookup"><span data-stu-id="12a83-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12a83-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12a83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12a83-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="12a83-106">[v] `mdTypeDef` Metadata token, který odkazuje na metadata třídy.</span><span class="sxs-lookup"><span data-stu-id="12a83-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="12a83-107">[out] Ukazatel na adresu ICorDebugClass objekt, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="12a83-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a83-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12a83-108">Requirements</span></span>  
 <span data-ttu-id="12a83-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12a83-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12a83-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12a83-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12a83-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12a83-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12a83-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12a83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
