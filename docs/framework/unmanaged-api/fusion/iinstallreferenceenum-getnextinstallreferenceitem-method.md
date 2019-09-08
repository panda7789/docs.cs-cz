---
title: IInstallReferenceEnum::GetNextInstallReferenceItem – metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20e2bff4257df64f761fd8fff880643d4e786748
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796455"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="a3dfd-102">IInstallReferenceEnum::GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="a3dfd-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="a3dfd-103">Získá ukazatel na další objekt [IInstallReferenceItem –](iinstallreferenceitem-interface.md) obsažený v tomto objektu [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a3dfd-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dfd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3dfd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3dfd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3dfd-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="a3dfd-106">mimo Vrácený `IInstallReferenceItem` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="a3dfd-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a3dfd-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a3dfd-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a3dfd-108">`dwFlags`musí mít hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="a3dfd-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a3dfd-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a3dfd-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a3dfd-110">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a3dfd-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3dfd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3dfd-111">Requirements</span></span>  
 <span data-ttu-id="a3dfd-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3dfd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3dfd-113">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a3dfd-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a3dfd-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3dfd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dfd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3dfd-115">See also</span></span>

- [<span data-ttu-id="a3dfd-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3dfd-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="a3dfd-117">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3dfd-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
