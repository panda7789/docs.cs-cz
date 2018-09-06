---
title: CorBindToCurrentRuntime – funkce
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 021f2b7a720c2190d56bdb2b35214c581a7b5f56
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872137"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="eb3d0-102">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="eb3d0-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="eb3d0-103">Načte modul CLR (CLR) do procesu pomocí informací o verzi uložených v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="eb3d0-104">Formát souboru XML je Modelováno podle konfiguračního souboru standardní aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="eb3d0-105">Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb3d0-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="eb3d0-106">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb3d0-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="eb3d0-107">Zobrazit [načítání modul CLR do procesu](https://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="eb3d0-107">See [Loading the Common Language Runtime into a Process](https://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb3d0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb3d0-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb3d0-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb3d0-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="eb3d0-110">[in] Název konfiguračního souboru aplikace, která určuje verzi modulu CLR pro načtení.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="eb3d0-111">Pokud název souboru není plně kvalifikovaná, předpokládá se, že se ve stejném adresáři jako spustitelný soubor uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="eb3d0-112">Atribut verze je popsán verzi modulu runtime, který se má načíst [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="eb3d0-113">Pokud není zadaná žádná verze, nebo pokud `<requiredRuntime>` nebyl nalezen element, načíst nejnovější verzi modulu CLR, který je nainstalován na počítači.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="eb3d0-114">[in] `CLSID` Třídy typu coclass, která implementuje [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="eb3d0-115">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="eb3d0-116">[in] `IID` Rozhraní, které jste požádali.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="eb3d0-117">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="eb3d0-118">[out] Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb3d0-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb3d0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb3d0-119">Requirements</span></span>  
 <span data-ttu-id="eb3d0-120">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb3d0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb3d0-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb3d0-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb3d0-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb3d0-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb3d0-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb3d0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb3d0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb3d0-124">See Also</span></span>  
 [<span data-ttu-id="eb3d0-125">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="eb3d0-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="eb3d0-126">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="eb3d0-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="eb3d0-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="eb3d0-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="eb3d0-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="eb3d0-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="eb3d0-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb3d0-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="eb3d0-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="eb3d0-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
