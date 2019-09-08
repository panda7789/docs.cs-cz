---
title: IAssemblyEnum::GetNextAssembly – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73c531378355100fdfca264ea9f96ff4d7c7ceda
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796688"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="52de4-102">IAssemblyEnum::GetNextAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="52de4-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="52de4-103">Získá ukazatel na další [IAssemblyName](iassemblyname-interface.md) obsažený v tomto objektu [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="52de4-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52de4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52de4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52de4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52de4-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="52de4-106">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="52de4-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="52de4-107">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="52de4-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="52de4-108">mimo Vrácený `IAssemblyName` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="52de4-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="52de4-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="52de4-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="52de4-110">`dwFlags`musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="52de4-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52de4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52de4-111">Requirements</span></span>  
 <span data-ttu-id="52de4-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52de4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52de4-113">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="52de4-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="52de4-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52de4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52de4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52de4-115">See also</span></span>

- [<span data-ttu-id="52de4-116">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52de4-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="52de4-117">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52de4-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
