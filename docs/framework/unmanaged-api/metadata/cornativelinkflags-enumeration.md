---
title: CorNativeLinkFlags – výčet
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6be71878ba354ebe53b4b8b9b40db3222ec828f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781740"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="c68b7-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="c68b7-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="c68b7-103">Obsahuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c68b7-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c68b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c68b7-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c68b7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c68b7-105">Members</span></span>  
  
|<span data-ttu-id="c68b7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c68b7-106">Member</span></span>|<span data-ttu-id="c68b7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c68b7-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="c68b7-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="c68b7-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="c68b7-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c68b7-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="c68b7-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c68b7-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="c68b7-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="c68b7-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c68b7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c68b7-112">Requirements</span></span>  
 <span data-ttu-id="c68b7-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c68b7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c68b7-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c68b7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c68b7-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c68b7-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c68b7-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c68b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c68b7-117">See also</span></span>

- [<span data-ttu-id="c68b7-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c68b7-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
