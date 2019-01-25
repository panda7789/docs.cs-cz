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
ms.openlocfilehash: 52b59a4e52d3e0cda7353ec1b39c5307bd7b218e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532263"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="58225-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="58225-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="58225-103">Obsahuje příznak hodnoty se používají pro registraci při instalaci modulu nebo složený image.</span><span class="sxs-lookup"><span data-stu-id="58225-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58225-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58225-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="58225-105">Členové</span><span class="sxs-lookup"><span data-stu-id="58225-105">Members</span></span>  
  
|<span data-ttu-id="58225-106">Člen</span><span class="sxs-lookup"><span data-stu-id="58225-106">Member</span></span>|<span data-ttu-id="58225-107">Popis</span><span class="sxs-lookup"><span data-stu-id="58225-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="58225-108">Určuje, že by neměl být soubory zkopírovány do cíle.</span><span class="sxs-lookup"><span data-stu-id="58225-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="58225-109">Určuje, že modul nebo složený konfigurace.</span><span class="sxs-lookup"><span data-stu-id="58225-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="58225-110">Určuje, zda modul nebo složený má odkazy na třídy.</span><span class="sxs-lookup"><span data-stu-id="58225-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58225-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58225-111">Requirements</span></span>  
 <span data-ttu-id="58225-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58225-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58225-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58225-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58225-114">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58225-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58225-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58225-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58225-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58225-116">See also</span></span>
- [<span data-ttu-id="58225-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="58225-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
