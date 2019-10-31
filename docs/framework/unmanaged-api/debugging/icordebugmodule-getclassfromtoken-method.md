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
ms.openlocfilehash: 790999093f874a4d81dd5db74ef012b1d997a12f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109645"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="7b1e4-102">ICorDebugModule::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="7b1e4-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="7b1e4-103">Získá třídu určenou tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="7b1e4-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b1e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b1e4-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="7b1e4-106">pro Token metadat `mdTypeDef`, který odkazuje na metadata třídy.</span><span class="sxs-lookup"><span data-stu-id="7b1e4-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="7b1e4-107">mimo Ukazatel na adresu objektu ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="7b1e4-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1e4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b1e4-108">Requirements</span></span>  
 <span data-ttu-id="7b1e4-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1e4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1e4-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b1e4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b1e4-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b1e4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b1e4-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1e4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
