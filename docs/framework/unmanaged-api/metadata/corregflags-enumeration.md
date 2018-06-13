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
ms.openlocfilehash: f7b935b8f59e434c9da364be1986dbed654a1efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445806"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="23ce6-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="23ce6-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="23ce6-103">Poskytuje příznak hodnoty používané pro registraci, při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="23ce6-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ce6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23ce6-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="23ce6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="23ce6-105">Members</span></span>  
  
|<span data-ttu-id="23ce6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="23ce6-106">Member</span></span>|<span data-ttu-id="23ce6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="23ce6-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="23ce6-108">Určuje, že soubory by neměly být zkopírovány do cílové.</span><span class="sxs-lookup"><span data-stu-id="23ce6-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="23ce6-109">Určuje, že modulu nebo složené je konfigurace.</span><span class="sxs-lookup"><span data-stu-id="23ce6-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="23ce6-110">Určuje, že modulu nebo složené obsahuje odkazy na třídy.</span><span class="sxs-lookup"><span data-stu-id="23ce6-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23ce6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23ce6-111">Requirements</span></span>  
 <span data-ttu-id="23ce6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ce6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ce6-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23ce6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23ce6-114">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23ce6-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23ce6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ce6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ce6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="23ce6-116">See Also</span></span>  
 [<span data-ttu-id="23ce6-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="23ce6-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
