---
title: CreateInstallReferenceEnum – funkce
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108570"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="400d4-102">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="400d4-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="400d4-103">Získá ukazatel na instanci [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) , která představuje seznam odkazů aplikace na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="400d4-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="400d4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="400d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="400d4-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="400d4-106">mimo Vrácený ukazatel `IInstallReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="400d4-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="400d4-107">pro [IAssemblyName](iassemblyname-interface.md) , který identifikuje sestavení, pro které mají být vyčísleny odkazy.</span><span class="sxs-lookup"><span data-stu-id="400d4-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="400d4-108">pro Příznaky ovlivňující chování čítače.</span><span class="sxs-lookup"><span data-stu-id="400d4-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="400d4-109">pro Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="400d4-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="400d4-110">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="400d4-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="400d4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="400d4-111">Requirements</span></span>  
 <span data-ttu-id="400d4-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="400d4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="400d4-113">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="400d4-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="400d4-114">**Knihovna:** Fusion. dll a knihovny Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="400d4-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="400d4-115">Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="400d4-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="400d4-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="400d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400d4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="400d4-117">See also</span></span>

- [<span data-ttu-id="400d4-118">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="400d4-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="400d4-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="400d4-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="400d4-120">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="400d4-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
