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
ms.openlocfilehash: 23d293a87112c62cb2127b435faeca258a7de226
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444220"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="f5eb6-102">AssemblyRefFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f5eb6-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="f5eb6-103">Obsahuje hodnoty, které popisují funkce odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5eb6-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5eb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5eb6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f5eb6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f5eb6-105">Members</span></span>  
  
|<span data-ttu-id="f5eb6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f5eb6-106">Member</span></span>|<span data-ttu-id="f5eb6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f5eb6-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="f5eb6-108">Určuje, že odkaz na sestavení obsahuje úplné a nehashované informace o vydavateli sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5eb6-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5eb6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5eb6-109">Requirements</span></span>  
 <span data-ttu-id="f5eb6-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5eb6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5eb6-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5eb6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5eb6-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5eb6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5eb6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5eb6-113">See also</span></span>

- [<span data-ttu-id="f5eb6-114">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f5eb6-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="f5eb6-115">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5eb6-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="f5eb6-116">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="f5eb6-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
