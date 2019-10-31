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
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134439"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="9b7cc-102">IAssemblyEnum::GetNextAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="9b7cc-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="9b7cc-103">Získá ukazatel na další [IAssemblyName](iassemblyname-interface.md) obsažený v tomto objektu [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b7cc-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b7cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b7cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b7cc-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="9b7cc-106">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9b7cc-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9b7cc-107">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="9b7cc-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9b7cc-108">mimo Vrácený ukazatel `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="9b7cc-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9b7cc-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9b7cc-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9b7cc-110">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="9b7cc-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b7cc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b7cc-111">Requirements</span></span>  
 <span data-ttu-id="9b7cc-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b7cc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7cc-113">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9b7cc-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9b7cc-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7cc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b7cc-115">See also</span></span>

- [<span data-ttu-id="9b7cc-116">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b7cc-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="9b7cc-117">IAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b7cc-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
