---
title: "LoadLibraryShim – funkce"
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
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b8fe8413d0eff332e60508a083f03574e58d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="f7ac7-102">LoadLibraryShim – funkce</span><span class="sxs-lookup"><span data-stu-id="f7ac7-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="f7ac7-103">Načte zadaný verzi knihovny DLL, která je součástí Distribuovatelný balíček .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="f7ac7-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7ac7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="f7ac7-105">Použití [iclrruntimeinfo::LoadLibrary –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7ac7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7ac7-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7ac7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7ac7-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="f7ac7-108">[v] Byl ukončen nula řetězec, který představuje název knihovnu DLL, která má být načten z knihovny rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="f7ac7-109">[v] Byl ukončen nula řetězec, který představuje verzi knihovny DLL pro načtení.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="f7ac7-110">Pokud `szVersion` je null, verze, vybraný pro načítání je nejnovější verze zadané knihovny DLL, která je nižší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="f7ac7-111">To znamená, jsou ignorovány všechny verze rovna nebo větší než verze 4, pokud `szVersion` má hodnotu null, a pokud je nainstalována žádná verze a nižší než verze 4, nepodaří načíst knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="f7ac7-112">To je potřeba zajistit, že instalace [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nemá vliv na existující aplikace nebo součásti.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="f7ac7-113">Naleznete v příspěvku [vnitroprocesovou SxS a migrace rychlý Start](http://go.microsoft.com/fwlink/?LinkId=200329) v blogu týmu CLR.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-113">See the entry [In-Proc SxS and Migration Quick Start](http://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f7ac7-114">Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="f7ac7-115">[out] Ukazatel na popisovač modulu.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7ac7-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7ac7-116">Return Value</span></span>  
 <span data-ttu-id="f7ac7-117">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f7ac7-118">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="f7ac7-118">Return code</span></span>|<span data-ttu-id="f7ac7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f7ac7-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f7ac7-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7ac7-120">S_OK</span></span>|<span data-ttu-id="f7ac7-121">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="f7ac7-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="f7ac7-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="f7ac7-123">Načítání `szDllName` vyžaduje načítání nelze načíst modul CLR (CLR) a potřebnou verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7ac7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7ac7-124">Remarks</span></span>  
 <span data-ttu-id="f7ac7-125">Tato funkce slouží k načtení knihovny DLL, které jsou součástí Distribuovatelný balíček .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="f7ac7-126">Nenačítá uživatelem generovaný knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ac7-127">Od verze rozhraní .NET Framework verze 2.0, načítání knihovna Fusion.dll způsobí, že CLR má být načten.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="f7ac7-128">Je to proto, že funkce v knihovně Fusion.dll jsou nyní obálky, jejíž implementace poskytované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="f7ac7-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7ac7-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7ac7-129">Requirements</span></span>  
 <span data-ttu-id="f7ac7-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7ac7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7ac7-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7ac7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7ac7-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7ac7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ac7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7ac7-133">See Also</span></span>  
 [<span data-ttu-id="f7ac7-134">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f7ac7-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
