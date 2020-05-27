---
title: CorRegFlags – výčet
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: d8d7a43848929e49a8cb48fb957f37213ac78f2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007348"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="04b4a-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="04b4a-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="04b4a-103">Poskytuje hodnoty příznaku používané k registraci při instalaci modulu nebo složené image.</span><span class="sxs-lookup"><span data-stu-id="04b4a-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04b4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04b4a-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="04b4a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="04b4a-105">Members</span></span>  
  
|<span data-ttu-id="04b4a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="04b4a-106">Member</span></span>|<span data-ttu-id="04b4a-107">Description</span><span class="sxs-lookup"><span data-stu-id="04b4a-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="04b4a-108">Určuje, že soubory by neměly být kopírovány do cílového umístění.</span><span class="sxs-lookup"><span data-stu-id="04b4a-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="04b4a-109">Určuje, že modul nebo kompozitní je konfigurace.</span><span class="sxs-lookup"><span data-stu-id="04b4a-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="04b4a-110">Určuje, že modul nebo složený z odkazů na třídy.</span><span class="sxs-lookup"><span data-stu-id="04b4a-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04b4a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04b4a-111">Requirements</span></span>  
 <span data-ttu-id="04b4a-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04b4a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04b4a-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04b4a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04b4a-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04b4a-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04b4a-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04b4a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b4a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b4a-116">See also</span></span>

- [<span data-ttu-id="04b4a-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="04b4a-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
