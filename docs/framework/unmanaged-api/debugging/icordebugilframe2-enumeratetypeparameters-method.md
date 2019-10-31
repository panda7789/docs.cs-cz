---
title: ICorDebugILFrame2::EnumerateTypeParameters – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 715ff5d4a06b53361d550f04e5154023d0b641bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095111"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="16fca-102">ICorDebugILFrame2::EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="16fca-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="16fca-103">Získá objekt ICorDebugTypeEnum, který obsahuje parametry <xref:System.Type> v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="16fca-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16fca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16fca-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16fca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16fca-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="16fca-106">Ukazatel na adresu objektu rozhraní ICorDebugTypeEnum, která umožňuje výčet parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="16fca-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="16fca-107">Seznam parametrů typu zahrnuje parametry typu třídy (pokud existují) následovaný parametry typu metody (pokud existují).</span><span class="sxs-lookup"><span data-stu-id="16fca-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16fca-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16fca-108">Remarks</span></span>  
 <span data-ttu-id="16fca-109">Použijte metodu [IMetaDataImport2:: EnumGenericParams –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) k určení, kolik parametrů typu třídy a parametrů typu metody tento seznam obsahuje.</span><span class="sxs-lookup"><span data-stu-id="16fca-109">Use the [IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="16fca-110">Parametry typu nejsou vždy k dispozici.</span><span class="sxs-lookup"><span data-stu-id="16fca-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16fca-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16fca-111">Requirements</span></span>  
 <span data-ttu-id="16fca-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16fca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16fca-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16fca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16fca-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16fca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16fca-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16fca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
