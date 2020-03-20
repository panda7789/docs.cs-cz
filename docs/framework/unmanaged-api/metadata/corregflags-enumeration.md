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
ms.openlocfilehash: 8fe6216e11a64ea182d796247d888b862b1e8377
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177931"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="a1737-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="a1737-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="a1737-103">Poskytuje hodnoty příznaku používané pro registraci při instalaci modulu nebo složené bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a1737-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1737-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1737-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a1737-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a1737-105">Members</span></span>  
  
|<span data-ttu-id="a1737-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a1737-106">Member</span></span>|<span data-ttu-id="a1737-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1737-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="a1737-108">Určuje, že soubory by neměly být zkopírovány do cíle.</span><span class="sxs-lookup"><span data-stu-id="a1737-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="a1737-109">Určuje, že modul nebo složený je konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a1737-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="a1737-110">Určuje, že modul nebo složený soubor obsahuje odkazy na třídy.</span><span class="sxs-lookup"><span data-stu-id="a1737-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1737-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1737-111">Requirements</span></span>  
 <span data-ttu-id="a1737-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1737-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1737-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="a1737-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1737-114">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1737-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1737-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1737-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1737-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1737-116">See also</span></span>

- [<span data-ttu-id="a1737-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a1737-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
