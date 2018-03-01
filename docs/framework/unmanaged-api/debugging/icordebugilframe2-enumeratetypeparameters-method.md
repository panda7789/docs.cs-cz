---
title: "ICorDebugILFrame2::EnumerateTypeParameters – metoda"
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
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9180ea68dde667ffe0dc8e15b98cb82efaa667ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="fefb0-102">ICorDebugILFrame2::EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="fefb0-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="fefb0-103">Získá objekt ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="fefb0-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fefb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fefb0-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fefb0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fefb0-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="fefb0-106">Ukazatel na adresu objekt rozhraní ICorDebugTypeEnum, která umožňuje výčet parametry typu.</span><span class="sxs-lookup"><span data-stu-id="fefb0-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="fefb0-107">Seznam parametrů typu zahrnují – třída typu parametry (pokud existuje) a typ parametry metody (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="fefb0-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fefb0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fefb0-108">Remarks</span></span>  
 <span data-ttu-id="fefb0-109">Použití [imetadataimport2::enumgenericparams –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) metoda k určení, kolik parametry typu třídy a metody zadejte parametry tento seznam obsahuje.</span><span class="sxs-lookup"><span data-stu-id="fefb0-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="fefb0-110">Parametry typu nejsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fefb0-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fefb0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fefb0-111">Requirements</span></span>  
 <span data-ttu-id="fefb0-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fefb0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fefb0-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fefb0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fefb0-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fefb0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fefb0-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fefb0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
