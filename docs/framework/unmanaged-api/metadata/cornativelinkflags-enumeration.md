---
title: "CorNativeLinkFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkFlags
helpviewer_keywords: CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09afda63959d974af71e0264ad116c20d3af1923
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="467af-102">CorNativeLinkFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="467af-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="467af-103">Poskytuje příznak hodnoty používané linkeru při propojování nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="467af-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="467af-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="467af-105">Členové</span><span class="sxs-lookup"><span data-stu-id="467af-105">Members</span></span>  
  
|<span data-ttu-id="467af-106">Člen</span><span class="sxs-lookup"><span data-stu-id="467af-106">Member</span></span>|<span data-ttu-id="467af-107">Popis</span><span class="sxs-lookup"><span data-stu-id="467af-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="467af-108">Označuje žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="467af-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="467af-109">Označuje `setLastError` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="467af-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="467af-110">Označuje `nomangle` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="467af-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="467af-111">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="467af-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="467af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="467af-112">Requirements</span></span>  
 <span data-ttu-id="467af-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="467af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="467af-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="467af-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="467af-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="467af-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="467af-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="467af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="467af-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="467af-117">See Also</span></span>  
 [<span data-ttu-id="467af-118">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="467af-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
