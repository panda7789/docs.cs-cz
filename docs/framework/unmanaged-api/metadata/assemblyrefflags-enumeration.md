---
title: AssemblyRefFlags – výčet
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 1307f555c9d8b6d28febcf25db89ae856c143d71
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009402"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="55fa0-102">AssemblyRefFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="55fa0-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="55fa0-103">Obsahuje hodnoty, které popisují funkce odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="55fa0-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55fa0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55fa0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="55fa0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="55fa0-105">Members</span></span>  
  
|<span data-ttu-id="55fa0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="55fa0-106">Member</span></span>|<span data-ttu-id="55fa0-107">Description</span><span class="sxs-lookup"><span data-stu-id="55fa0-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="55fa0-108">Určuje, že odkaz na sestavení obsahuje úplné a nehashované informace o vydavateli sestavení.</span><span class="sxs-lookup"><span data-stu-id="55fa0-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55fa0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55fa0-109">Requirements</span></span>  
 <span data-ttu-id="55fa0-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55fa0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55fa0-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="55fa0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55fa0-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55fa0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fa0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="55fa0-113">See also</span></span>

- [<span data-ttu-id="55fa0-114">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="55fa0-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="55fa0-115">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55fa0-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="55fa0-116">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="55fa0-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)
