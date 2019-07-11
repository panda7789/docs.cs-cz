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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf2a1bca6115902d96f72c19dc469d0a1c8588cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756213"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="b1c11-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="b1c11-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="b1c11-103">Obsahuje příznak hodnoty se používají pro registraci při instalaci modulu nebo složený image.</span><span class="sxs-lookup"><span data-stu-id="b1c11-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1c11-104">Syntax</span></span>  
  
```cpp  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b1c11-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b1c11-105">Members</span></span>  
  
|<span data-ttu-id="b1c11-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b1c11-106">Member</span></span>|<span data-ttu-id="b1c11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b1c11-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="b1c11-108">Určuje, že by neměl být soubory zkopírovány do cíle.</span><span class="sxs-lookup"><span data-stu-id="b1c11-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="b1c11-109">Určuje, že modul nebo složený konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b1c11-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="b1c11-110">Určuje, zda modul nebo složený má odkazy na třídy.</span><span class="sxs-lookup"><span data-stu-id="b1c11-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1c11-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1c11-111">Requirements</span></span>  
 <span data-ttu-id="b1c11-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c11-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c11-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1c11-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1c11-114">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1c11-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1c11-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c11-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c11-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1c11-116">See also</span></span>

- [<span data-ttu-id="b1c11-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b1c11-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
