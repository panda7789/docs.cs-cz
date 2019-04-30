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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7820b33dcfacae5ede5235607e40d95940fc474
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771901"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="8540d-102">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="8540d-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="8540d-103">Získá ukazatel [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam aplikace odkazy na zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="8540d-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8540d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8540d-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8540d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8540d-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="8540d-106">[out] Vrácený `IInstallReferenceEnum` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="8540d-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="8540d-107">[in] [Iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) , který identifikuje sestavení, pro které chcete získat výčet odkazy.</span><span class="sxs-lookup"><span data-stu-id="8540d-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8540d-108">[in] Příznaky, které ovlivňují chování čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="8540d-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="8540d-109">[in] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8540d-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="8540d-110">`pvReserved` musí být referencí s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8540d-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8540d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8540d-111">Requirements</span></span>  
 <span data-ttu-id="8540d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8540d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8540d-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8540d-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8540d-114">**Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="8540d-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="8540d-115">Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="8540d-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="8540d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8540d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8540d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8540d-117">See also</span></span>

- [<span data-ttu-id="8540d-118">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8540d-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [<span data-ttu-id="8540d-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8540d-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="8540d-120">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="8540d-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
