---
title: COUNINITIEE – výčet
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176120"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="eab20-102">COUNINITIEE – výčet</span><span class="sxs-lookup"><span data-stu-id="eab20-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="eab20-103">Určuje konstanty používané [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) při inicializaci běžného jazyku runtime.</span><span class="sxs-lookup"><span data-stu-id="eab20-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab20-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="eab20-105">Členové</span><span class="sxs-lookup"><span data-stu-id="eab20-105">Members</span></span>  
  
|<span data-ttu-id="eab20-106">Člen</span><span class="sxs-lookup"><span data-stu-id="eab20-106">Member</span></span>|<span data-ttu-id="eab20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="eab20-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="eab20-108">Označuje výchozí režim neinicializace.</span><span class="sxs-lookup"><span data-stu-id="eab20-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="eab20-109">Označuje režim neinicializace pro uvolnění sestavy.</span><span class="sxs-lookup"><span data-stu-id="eab20-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eab20-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eab20-110">Requirements</span></span>  
 <span data-ttu-id="eab20-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab20-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab20-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="eab20-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eab20-113">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eab20-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eab20-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab20-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab20-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eab20-115">See also</span></span>

- [<span data-ttu-id="eab20-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="eab20-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
