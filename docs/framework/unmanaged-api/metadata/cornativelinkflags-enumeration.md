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
ms.openlocfilehash: 9211af4726617598f3dd8772383cade6368e6c08
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007621"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="6fa27-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="6fa27-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="6fa27-103">Poskytuje hodnoty příznaků používané linkerem při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6fa27-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fa27-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6fa27-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6fa27-105">Members</span></span>  
  
|<span data-ttu-id="6fa27-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6fa27-106">Member</span></span>|<span data-ttu-id="6fa27-107">Description</span><span class="sxs-lookup"><span data-stu-id="6fa27-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="6fa27-108">Neindikuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="6fa27-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="6fa27-109">Označuje `setLastError` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6fa27-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="6fa27-110">Označuje `nomangle` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6fa27-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="6fa27-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="6fa27-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6fa27-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fa27-112">Requirements</span></span>  
 <span data-ttu-id="6fa27-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa27-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa27-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6fa27-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fa27-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6fa27-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fa27-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa27-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fa27-117">See also</span></span>

- [<span data-ttu-id="6fa27-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="6fa27-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
