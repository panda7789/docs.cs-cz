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
ms.openlocfilehash: f8a56dcf03748c6582bce07fc379113c5cdddd11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212593"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="cc4f6-102">ICorDebugModule::GetClassFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="cc4f6-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="cc4f6-103">Získá třídu určenou tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="cc4f6-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc4f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc4f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc4f6-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="cc4f6-106">pro `mdTypeDef`Token metadat, který odkazuje na metadata třídy.</span><span class="sxs-lookup"><span data-stu-id="cc4f6-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="cc4f6-107">mimo Ukazatel na adresu objektu ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="cc4f6-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4f6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc4f6-108">Requirements</span></span>  
 <span data-ttu-id="cc4f6-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc4f6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4f6-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc4f6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc4f6-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc4f6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc4f6-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc4f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
