---
title: "CreateInstallReferenceEnum – funkce"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a0c902cf5d9d8b6295cab95552aae6775c5bf889
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="c67d8-102">CreateInstallReferenceEnum – funkce</span><span class="sxs-lookup"><span data-stu-id="c67d8-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="c67d8-103">Získá odkazy [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam odkazů aplikace na zadaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="c67d8-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c67d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c67d8-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c67d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c67d8-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="c67d8-106">[out] Vrácený `IInstallReferenceEnum` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="c67d8-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="c67d8-107">[v] [Iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) , identifikuje sestavení, pro které chcete vytvořit výčet odkazy.</span><span class="sxs-lookup"><span data-stu-id="c67d8-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c67d8-108">[v] Příznaky, které ovlivňují chování enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c67d8-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c67d8-109">[v] Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c67d8-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c67d8-110">`pvReserved`musí být odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="c67d8-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c67d8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c67d8-111">Requirements</span></span>  
 <span data-ttu-id="c67d8-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c67d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c67d8-113">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c67d8-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c67d8-114">**Knihovna:** knihovna Fusion.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="c67d8-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="c67d8-115">Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c67d8-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c67d8-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c67d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c67d8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c67d8-117">See Also</span></span>  
 [<span data-ttu-id="c67d8-118">IInstallReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c67d8-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="c67d8-119">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c67d8-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="c67d8-120">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="c67d8-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
