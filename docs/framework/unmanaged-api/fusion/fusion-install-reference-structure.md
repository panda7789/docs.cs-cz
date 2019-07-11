---
title: FUSION_INSTALL_REFERENCE – struktura
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec18d5d5a6574cb0e08a6c4d6eaedcbcbf6886cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759362"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="f9d43-102">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="f9d43-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="f9d43-103">Představuje odkaz, který aplikace slouží k sestavení aplikace nainstalované v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9d43-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9d43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9d43-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="f9d43-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f9d43-105">Members</span></span>  
  
|<span data-ttu-id="f9d43-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f9d43-106">Member</span></span>|<span data-ttu-id="f9d43-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9d43-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f9d43-108">Velikost struktury v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f9d43-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="f9d43-109">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f9d43-109">Reserved for future extensibility.</span></span> <span data-ttu-id="f9d43-110">Tato hodnota musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="f9d43-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="f9d43-111">Entita, která přidá odkaz.</span><span class="sxs-lookup"><span data-stu-id="f9d43-111">The entity that adds the reference.</span></span> <span data-ttu-id="f9d43-112">Toto pole může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="f9d43-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="f9d43-113">-   FUSION_REFCOUNT_MSI_GUID: Sestavení se odkazuje aplikaci, která byla nainstalována pomocí Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d43-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="f9d43-114">`szIdentifier` Je nastaveno na `MSI`a `szNonCanonicalData` je nastaveno na `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="f9d43-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="f9d43-115">Toto schéma se používá pro sestavení vedle sebe Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d43-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="f9d43-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Sestavení se odkazuje, který se zobrazí v aplikaci **přidat nebo odebrat programy** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9d43-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="f9d43-117">`szIdentifier` Pole obsahuje token, který zaregistruje aplikaci **přidat nebo odebrat programy** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f9d43-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="f9d43-118">-   FUSION_REFCOUNT_FILEPATH_GUID: Sestavení se odkazuje v aplikaci, která je reprezentována souboru v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="f9d43-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="f9d43-119">`szIdentifier` Pole obsahuje cestu k tomuto souboru.</span><span class="sxs-lookup"><span data-stu-id="f9d43-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="f9d43-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Aplikace, která je reprezentována pouze neprůhledný řetězec odkazuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9d43-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="f9d43-121">`szIdentifier` Pole obsahuje tento neprůhledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f9d43-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="f9d43-122">Když odeberete tato hodnota nekontroluje existenci neprůhledné odkazy na globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9d43-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="f9d43-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je rezervovaná.</span><span class="sxs-lookup"><span data-stu-id="f9d43-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="f9d43-124">Jedinečný řetězec, který identifikuje aplikaci, která nainstalovaná sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9d43-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="f9d43-125">Jeho hodnota závisí na hodnotě `guidScheme` pole.</span><span class="sxs-lookup"><span data-stu-id="f9d43-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="f9d43-126">Řetězec, který je srozumitelné pouze entity, která přidá odkaz.</span><span class="sxs-lookup"><span data-stu-id="f9d43-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="f9d43-127">Globální mezipaměti sestavení ukládá tento řetězec, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f9d43-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9d43-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9d43-128">Requirements</span></span>  
 <span data-ttu-id="f9d43-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9d43-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d43-130">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f9d43-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f9d43-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d43-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d43-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9d43-132">See also</span></span>

- [<span data-ttu-id="f9d43-133">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="f9d43-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="f9d43-134">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="f9d43-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
