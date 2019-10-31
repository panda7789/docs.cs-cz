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
ms.openlocfilehash: 0dad50f1acac38f8cdc505026e88d42882deb580
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131721"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="66401-102">IInstallReferenceEnum::GetNextInstallReferenceItem – metoda</span><span class="sxs-lookup"><span data-stu-id="66401-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="66401-103">Získá ukazatel na další objekt [IInstallReferenceItem –](iinstallreferenceitem-interface.md) obsažený v tomto objektu [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="66401-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66401-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66401-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66401-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66401-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="66401-106">mimo Vrácený ukazatel `IInstallReferenceItem`.</span><span class="sxs-lookup"><span data-stu-id="66401-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="66401-107">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="66401-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="66401-108">`dwFlags` musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="66401-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="66401-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="66401-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="66401-110">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="66401-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66401-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66401-111">Requirements</span></span>  
 <span data-ttu-id="66401-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66401-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66401-113">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="66401-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="66401-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66401-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66401-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66401-115">See also</span></span>

- [<span data-ttu-id="66401-116">IInstallReferenceItem – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66401-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="66401-117">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66401-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
