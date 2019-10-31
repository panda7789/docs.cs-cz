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
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138322"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="a349f-102">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="a349f-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="a349f-103">Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi uložených v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="a349f-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="a349f-104">Formát souboru XML je modelován po standardní konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="a349f-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="a349f-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="a349f-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="a349f-106">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a349f-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="a349f-107">Viz [načtení modulu CLR (Common Language Runtime) do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a349f-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a349f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a349f-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a349f-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="a349f-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="a349f-110">pro Název konfiguračního souboru aplikace, který určuje verzi modulu CLR, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="a349f-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="a349f-111">Pokud název souboru není plně kvalifikovaný, předpokládá se, že se nachází ve stejném adresáři jako spustitelný soubor, který volání provádí.</span><span class="sxs-lookup"><span data-stu-id="a349f-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="a349f-112">Verze modulu runtime, která má být načtena, je popsána atributem verze v [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a349f-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="a349f-113">Pokud není zadána žádná verze nebo pokud `<requiredRuntime>` element nebyl nalezen, je načtena nejnovější verze CLR, která je nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="a349f-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a349f-114">pro `CLSID` třídy coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a349f-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a349f-115">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a349f-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a349f-116">pro `IID` rozhraní, které požadujete.</span><span class="sxs-lookup"><span data-stu-id="a349f-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="a349f-117">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a349f-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a349f-118">mimo Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a349f-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a349f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a349f-119">Requirements</span></span>  
 <span data-ttu-id="a349f-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a349f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a349f-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a349f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a349f-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a349f-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a349f-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a349f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a349f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a349f-124">See also</span></span>

- [<span data-ttu-id="a349f-125">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="a349f-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="a349f-126">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="a349f-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="a349f-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="a349f-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="a349f-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="a349f-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="a349f-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a349f-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="a349f-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="a349f-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
