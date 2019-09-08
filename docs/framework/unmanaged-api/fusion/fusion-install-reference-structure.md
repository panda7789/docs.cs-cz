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
ms.openlocfilehash: 9e81fb7c99b9fd03a69456a84f2191770f40121d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795345"
---
# <a name="fusion_install_reference-structure"></a><span data-ttu-id="9096d-102">FUSION_INSTALL_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="9096d-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="9096d-103">Představuje odkaz, který aplikace provede na sestavení, které aplikace nainstalovala v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9096d-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9096d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9096d-104">Syntax</span></span>  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="9096d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9096d-105">Members</span></span>  
  
|<span data-ttu-id="9096d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9096d-106">Member</span></span>|<span data-ttu-id="9096d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9096d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="9096d-108">Velikost struktury v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9096d-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="9096d-109">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="9096d-109">Reserved for future extensibility.</span></span> <span data-ttu-id="9096d-110">Tato hodnota musí být 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="9096d-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="9096d-111">Entita, která přidá odkaz</span><span class="sxs-lookup"><span data-stu-id="9096d-111">The entity that adds the reference.</span></span> <span data-ttu-id="9096d-112">V tomto poli může být jedna z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="9096d-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="9096d-113">-   FUSION_REFCOUNT_MSI_GUID: Na sestavení odkazuje aplikace, která byla nainstalována pomocí Instalační služba systému Windows Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9096d-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="9096d-114">Pole je nastaveno na `MSI`hodnotu a `szNonCanonicalData` pole je nastaveno na `Windows Installer`. `szIdentifier`</span><span class="sxs-lookup"><span data-stu-id="9096d-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="9096d-115">Toto schéma se používá pro souběžná sestavení Windows.</span><span class="sxs-lookup"><span data-stu-id="9096d-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="9096d-116">- FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Na sestavení odkazuje aplikace, která se zobrazí v rozhraní **Přidat nebo odebrat programy** .</span><span class="sxs-lookup"><span data-stu-id="9096d-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="9096d-117">Pole poskytuje token, který registruje aplikaci pomocí rozhraní **Přidat nebo odebrat programy.** `szIdentifier`</span><span class="sxs-lookup"><span data-stu-id="9096d-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="9096d-118">-   FUSION_REFCOUNT_FILEPATH_GUID: Na sestavení se odkazuje aplikace, která je reprezentovaná souborem v systému souborů.</span><span class="sxs-lookup"><span data-stu-id="9096d-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="9096d-119">`szIdentifier` Pole poskytuje cestu k tomuto souboru.</span><span class="sxs-lookup"><span data-stu-id="9096d-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="9096d-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Na sestavení odkazuje aplikace, která je zastoupena pouze neprůhledným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="9096d-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="9096d-121">`szIdentifier` Pole poskytuje tento neprůhledný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9096d-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="9096d-122">Globální mezipaměť sestavení (GAC) neprovádí kontrolu existence neprůhledných odkazů při odebrání této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9096d-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="9096d-123">- FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="9096d-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="9096d-124">Jedinečný řetězec, který identifikuje aplikaci, která nainstalovala sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9096d-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="9096d-125">Jeho hodnota závisí na hodnotě `guidScheme` pole.</span><span class="sxs-lookup"><span data-stu-id="9096d-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="9096d-126">Řetězec, který rozumí pouze entita, která přidá odkaz.</span><span class="sxs-lookup"><span data-stu-id="9096d-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="9096d-127">Globální mezipaměť sestavení (GAC) ukládá tento řetězec, ale nepoužívá ho.</span><span class="sxs-lookup"><span data-stu-id="9096d-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9096d-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9096d-128">Requirements</span></span>  
 <span data-ttu-id="9096d-129">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9096d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9096d-130">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9096d-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9096d-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9096d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9096d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9096d-132">See also</span></span>

- [<span data-ttu-id="9096d-133">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="9096d-133">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="9096d-134">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="9096d-134">Global Assembly Cache</span></span>](../../app-domains/gac.md)
