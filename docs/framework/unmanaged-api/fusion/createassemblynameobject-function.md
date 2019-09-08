---
title: CreateAssemblyNameObject – funkce
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb53014a28fb291b8463535addfb61e62d32d7d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795351"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="cc612-102">CreateAssemblyNameObject – funkce</span><span class="sxs-lookup"><span data-stu-id="cc612-102">CreateAssemblyNameObject Function</span></span>
<span data-ttu-id="cc612-103">Získá ukazatel rozhraní na instanci [IAssemblyName](iassemblyname-interface.md) , která představuje jedinečnou identitu sestavení se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="cc612-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc612-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc612-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc612-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc612-105">Parameters</span></span>  
 `ppAssemblyNameObj`  
 <span data-ttu-id="cc612-106">mimo Vráceno `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="cc612-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="cc612-107">pro Název sestavení, pro které chcete vytvořit novou `IAssemblyName` instanci.</span><span class="sxs-lookup"><span data-stu-id="cc612-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cc612-108">pro Příznaky, které mají být předána konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="cc612-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cc612-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="cc612-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cc612-110">`pvReserved`musí se jednat o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="cc612-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc612-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc612-111">Requirements</span></span>  
 <span data-ttu-id="cc612-112">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc612-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc612-113">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cc612-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cc612-114">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc612-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc612-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc612-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc612-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc612-116">See also</span></span>

- [<span data-ttu-id="cc612-117">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc612-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="cc612-118">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="cc612-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
