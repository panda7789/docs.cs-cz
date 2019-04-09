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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151993"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="41eec-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="41eec-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="41eec-103">Obsahuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="41eec-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41eec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41eec-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="41eec-105">Členové</span><span class="sxs-lookup"><span data-stu-id="41eec-105">Members</span></span>  
  
|<span data-ttu-id="41eec-106">Člen</span><span class="sxs-lookup"><span data-stu-id="41eec-106">Member</span></span>|<span data-ttu-id="41eec-107">Popis</span><span class="sxs-lookup"><span data-stu-id="41eec-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="41eec-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="41eec-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="41eec-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="41eec-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="41eec-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="41eec-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="41eec-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="41eec-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41eec-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41eec-112">Requirements</span></span>  
 <span data-ttu-id="41eec-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41eec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41eec-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="41eec-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41eec-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41eec-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="41eec-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="41eec-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41eec-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41eec-117">See also</span></span>

- [<span data-ttu-id="41eec-118">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="41eec-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
