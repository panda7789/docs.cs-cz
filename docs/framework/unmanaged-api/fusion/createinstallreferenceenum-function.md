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
ms.openlocfilehash: e35654b03f68a306329ef488289cfecd6f012484
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431571"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="d6265-102">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="d6265-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="d6265-103">Získá odkazy [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam odkazů aplikace na zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6265-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6265-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6265-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6265-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6265-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="d6265-106">[out] Vrácený `IInstallReferenceEnum` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="d6265-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="d6265-107">[v] [Iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) , identifikuje sestavení, pro které chcete vytvořit výčet odkazy.</span><span class="sxs-lookup"><span data-stu-id="d6265-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d6265-108">[v] Příznaky, které ovlivňují chování enumerátor.</span><span class="sxs-lookup"><span data-stu-id="d6265-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d6265-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d6265-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d6265-110">`pvReserved` musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d6265-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6265-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6265-111">Requirements</span></span>  
 <span data-ttu-id="d6265-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6265-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6265-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d6265-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6265-114">**Knihovna:** knihovna Fusion.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="d6265-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="d6265-115">Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6265-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d6265-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6265-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6265-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6265-117">See Also</span></span>  
 [<span data-ttu-id="d6265-118">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6265-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="d6265-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6265-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="d6265-120">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="d6265-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
