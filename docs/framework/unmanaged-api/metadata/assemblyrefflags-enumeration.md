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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043313"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="512ab-102">AssemblyRefFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="512ab-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="512ab-103">Obsahuje hodnoty, které popisují funkce odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="512ab-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="512ab-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="512ab-105">Členové</span><span class="sxs-lookup"><span data-stu-id="512ab-105">Members</span></span>  
  
|<span data-ttu-id="512ab-106">Člen</span><span class="sxs-lookup"><span data-stu-id="512ab-106">Member</span></span>|<span data-ttu-id="512ab-107">Popis</span><span class="sxs-lookup"><span data-stu-id="512ab-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="512ab-108">Určuje, že odkaz na sestavení obsahuje nezašifrované, úplné informace o vydavateli sestavení.</span><span class="sxs-lookup"><span data-stu-id="512ab-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="512ab-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="512ab-109">Requirements</span></span>  
 <span data-ttu-id="512ab-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512ab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512ab-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="512ab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="512ab-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512ab-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512ab-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="512ab-113">See also</span></span>

- [<span data-ttu-id="512ab-114">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="512ab-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="512ab-115">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="512ab-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="512ab-116">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="512ab-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
