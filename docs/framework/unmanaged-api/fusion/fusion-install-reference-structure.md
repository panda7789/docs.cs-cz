---
title: "FUSION_INSTALL_REFERENCE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FUSION_INSTALL_REFERENCE
api_location: fusion.dll
api_type: COM
f1_keywords: FUSION_INSTALL_REFERENCE
helpviewer_keywords: FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 244ea215b6668685920a454c1bd9da065076f38b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="8be29-102">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="8be29-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="8be29-103">Představuje odkaz, který umožňuje aplikaci na sestavení, který má aplikace nainstalované v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8be29-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8be29-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="8be29-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8be29-105">Members</span></span>  
  
|<span data-ttu-id="8be29-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8be29-106">Member</span></span>|<span data-ttu-id="8be29-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8be29-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="8be29-108">Velikost struktury v bajtech.</span><span class="sxs-lookup"><span data-stu-id="8be29-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="8be29-109">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8be29-109">Reserved for future extensibility.</span></span> <span data-ttu-id="8be29-110">Tato hodnota musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="8be29-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="8be29-111">Typ entity, která přidá odkaz.</span><span class="sxs-lookup"><span data-stu-id="8be29-111">The entity that adds the reference.</span></span> <span data-ttu-id="8be29-112">Toto pole může mít jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="8be29-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="8be29-113">-FUSION_REFCOUNT_MSI_GUID: Odkazuje sestavení aplikace, která byla nainstalována pomocí Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8be29-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="8be29-114">`szIdentifier` Je nastaveno na `MSI`a `szNonCanonicalData` je nastaveno na `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="8be29-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="8be29-115">Toto schéma se používá pro Windows souběžně sdílená sestavení.</span><span class="sxs-lookup"><span data-stu-id="8be29-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="8be29-116">-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Sestavení odkazuje aplikace, která se zobrazí v **přidat nebo odebrat programy** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8be29-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="8be29-117">`szIdentifier` Pole poskytuje token, který aplikace se zaregistruje **přidat nebo odebrat programy** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8be29-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="8be29-118">-FUSION_REFCOUNT_FILEPATH_GUID: Odkazuje sestavení aplikace, která je reprezentována souboru v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="8be29-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="8be29-119">`szIdentifier` Pole obsahuje cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="8be29-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="8be29-120">-FUSION_REFCOUNT_OPAQUE_STRING_GUID: Odkazuje sestavení aplikace, která je reprezentována pouze neprůhledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8be29-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="8be29-121">`szIdentifier` Pole poskytuje toto neprůhledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8be29-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="8be29-122">Když odeberete tuto hodnotu nekontroluje existenci neprůhledného odkazy globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8be29-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="8be29-123">-FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je rezervovaná.</span><span class="sxs-lookup"><span data-stu-id="8be29-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="8be29-124">Jedinečného řetězce, který identifikuje aplikaci, která nainstalována sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="8be29-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="8be29-125">Jeho hodnota závisí na hodnotu `guidScheme` pole.</span><span class="sxs-lookup"><span data-stu-id="8be29-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="8be29-126">Řetězec, který se rozumí pouze typ entity, která přidá odkaz.</span><span class="sxs-lookup"><span data-stu-id="8be29-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="8be29-127">Globální mezipaměti sestavení ukládá tento řetězec, ale nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8be29-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8be29-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8be29-128">Requirements</span></span>  
 <span data-ttu-id="8be29-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be29-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be29-130">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8be29-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8be29-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be29-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be29-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8be29-132">See Also</span></span>  
 [<span data-ttu-id="8be29-133">Struktury fúzí</span><span class="sxs-lookup"><span data-stu-id="8be29-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="8be29-134">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="8be29-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
