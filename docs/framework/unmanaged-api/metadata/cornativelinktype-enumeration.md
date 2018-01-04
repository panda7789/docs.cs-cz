---
title: "CorNativeLinkType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkType
helpviewer_keywords: CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f19a4366958249881c1f4c33919f239f33c21b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="b6af6-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="b6af6-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="b6af6-103">Obsahuje hodnoty, které označují typ propojené v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="b6af6-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6af6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6af6-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="b6af6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b6af6-105">Members</span></span>  
  
|<span data-ttu-id="b6af6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b6af6-106">Member</span></span>|<span data-ttu-id="b6af6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b6af6-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="b6af6-108">Označuje, že žádný z klíčová slova nejsou zadány.</span><span class="sxs-lookup"><span data-stu-id="b6af6-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="b6af6-109">Označuje, že je zadané klíčové slovo ANSI.</span><span class="sxs-lookup"><span data-stu-id="b6af6-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="b6af6-110">Určuje, zda je zadán Unicode – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="b6af6-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="b6af6-111">Určuje, zda je zadán auto – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b6af6-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="b6af6-112">Označuje, že je zadané klíčové slovo OLE.</span><span class="sxs-lookup"><span data-stu-id="b6af6-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="b6af6-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="b6af6-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6af6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6af6-114">Requirements</span></span>  
 <span data-ttu-id="b6af6-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6af6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6af6-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6af6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6af6-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6af6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6af6-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6af6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6af6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6af6-119">See Also</span></span>  
 [<span data-ttu-id="b6af6-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b6af6-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
