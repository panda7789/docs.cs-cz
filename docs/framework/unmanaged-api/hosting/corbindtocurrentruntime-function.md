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
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493562"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="fb309-102">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="fb309-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="fb309-103">Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi uložených v souboru XML.</span><span class="sxs-lookup"><span data-stu-id="fb309-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="fb309-104">Formát souboru XML je modelován po standardní konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb309-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="fb309-105">Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb309-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="fb309-106">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fb309-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="fb309-107">Viz [načtení modulu CLR (Common Language Runtime) do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fb309-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb309-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb309-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb309-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb309-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="fb309-110">pro Název konfiguračního souboru aplikace, který určuje verzi modulu CLR, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="fb309-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="fb309-111">Pokud název souboru není plně kvalifikovaný, předpokládá se, že se nachází ve stejném adresáři jako spustitelný soubor, který volání provádí.</span><span class="sxs-lookup"><span data-stu-id="fb309-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="fb309-112">Verze modulu runtime, která má být načtena, je popsána atributem verze v [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="fb309-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="fb309-113">Pokud není zadána žádná verze nebo pokud `<requiredRuntime>` prvek nelze nalézt, je načtena nejnovější verze CLR, která je nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="fb309-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="fb309-114">pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fb309-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="fb309-115">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="fb309-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="fb309-116">pro `IID`Rozhraní, které požadujete.</span><span class="sxs-lookup"><span data-stu-id="fb309-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="fb309-117">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="fb309-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="fb309-118">mimo Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb309-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb309-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb309-119">Requirements</span></span>  
 <span data-ttu-id="fb309-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb309-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb309-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb309-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb309-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb309-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb309-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb309-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb309-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb309-124">See also</span></span>

- [<span data-ttu-id="fb309-125">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="fb309-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="fb309-126">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="fb309-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="fb309-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="fb309-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="fb309-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="fb309-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="fb309-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb309-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="fb309-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="fb309-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
