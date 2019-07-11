---
title: CorNativeLinkType – výčet
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 944c641c39ddef7add0e9f382dc7d35068668455
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781718"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9160c-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="9160c-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="9160c-103">Obsahuje hodnoty, které označují typ propojené v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="9160c-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9160c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9160c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="9160c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9160c-105">Members</span></span>  
  
|<span data-ttu-id="9160c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9160c-106">Member</span></span>|<span data-ttu-id="9160c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9160c-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9160c-108">Označuje, že jsou zadána žádná klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="9160c-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9160c-109">Určuje, zda je zadán ANSI – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9160c-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9160c-110">Určuje, zda je zadán Unicode – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="9160c-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9160c-111">Určuje, zda je zadán klíčovým slovem auto.</span><span class="sxs-lookup"><span data-stu-id="9160c-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9160c-112">Označuje, zda je zadán klíčovým slovem OLE.</span><span class="sxs-lookup"><span data-stu-id="9160c-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9160c-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="9160c-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9160c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9160c-114">Requirements</span></span>  
 <span data-ttu-id="9160c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9160c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9160c-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9160c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9160c-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9160c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9160c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9160c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9160c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9160c-119">See also</span></span>

- [<span data-ttu-id="9160c-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9160c-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
