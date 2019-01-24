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
ms.openlocfilehash: b31df454c49ddccc74a7e877c09efa4f45b69d9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491791"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="0d7e0-102">AssemblyRefFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="0d7e0-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="0d7e0-103">Obsahuje hodnoty, které popisují funkce odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d7e0-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0d7e0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0d7e0-105">Members</span></span>  
  
|<span data-ttu-id="0d7e0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0d7e0-106">Member</span></span>|<span data-ttu-id="0d7e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0d7e0-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="0d7e0-108">Určuje, že odkaz na sestavení obsahuje nezašifrované, úplné informace o vydavateli sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d7e0-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d7e0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d7e0-109">Requirements</span></span>  
 <span data-ttu-id="0d7e0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d7e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d7e0-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d7e0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d7e0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d7e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7e0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d7e0-113">See also</span></span>
- [<span data-ttu-id="0d7e0-114">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="0d7e0-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="0d7e0-115">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d7e0-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="0d7e0-116">DefineAssemblyRef – metoda</span><span class="sxs-lookup"><span data-stu-id="0d7e0-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
