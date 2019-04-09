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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128892"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="315c5-102">AssemblyRefFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="315c5-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="315c5-103">Obsahuje hodnoty, které popisují funkce odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="315c5-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="315c5-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="315c5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="315c5-105">Members</span></span>  
  
|<span data-ttu-id="315c5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="315c5-106">Member</span></span>|<span data-ttu-id="315c5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="315c5-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="315c5-108">Určuje, že odkaz na sestavení obsahuje nezašifrované, úplné informace o vydavateli sestavení.</span><span class="sxs-lookup"><span data-stu-id="315c5-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="315c5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="315c5-109">Requirements</span></span>  
 <span data-ttu-id="315c5-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="315c5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="315c5-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="315c5-111">**Header:** Cor.h</span></span>  
  
 **<span data-ttu-id="315c5-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="315c5-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="315c5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="315c5-113">See also</span></span>

- [<span data-ttu-id="315c5-114">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="315c5-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="315c5-115">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="315c5-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="315c5-116">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="315c5-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
