---
title: CorNativeLinkFlags – výčet
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e6eb2a30dd6722309fd80c1611ad9200ab14ae5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045445"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="16122-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="16122-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="16122-103">Obsahuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="16122-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16122-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16122-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="16122-105">Členové</span><span class="sxs-lookup"><span data-stu-id="16122-105">Members</span></span>  
  
|<span data-ttu-id="16122-106">Člen</span><span class="sxs-lookup"><span data-stu-id="16122-106">Member</span></span>|<span data-ttu-id="16122-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16122-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="16122-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="16122-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="16122-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="16122-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="16122-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="16122-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="16122-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="16122-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16122-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16122-112">Requirements</span></span>  
 <span data-ttu-id="16122-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16122-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16122-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16122-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16122-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16122-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16122-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16122-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16122-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16122-117">See also</span></span>

- [<span data-ttu-id="16122-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="16122-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
