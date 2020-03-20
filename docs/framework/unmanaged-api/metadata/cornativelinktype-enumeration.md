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
ms.openlocfilehash: 0b613ebacdff82a29fdbc3f4caa0f2b8bb5d3f6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176159"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="2092c-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="2092c-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="2092c-103">Poskytuje hodnoty, které označují typ propojený v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="2092c-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2092c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2092c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2092c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2092c-105">Members</span></span>  
  
|<span data-ttu-id="2092c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2092c-106">Member</span></span>|<span data-ttu-id="2092c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2092c-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="2092c-108">Označuje, že žádné z klíčových slov jsou zadány.</span><span class="sxs-lookup"><span data-stu-id="2092c-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="2092c-109">Označuje, že je zadáno klíčové slovo ANSI.</span><span class="sxs-lookup"><span data-stu-id="2092c-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="2092c-110">Označuje, že je zadáno klíčové slovo Unicode.</span><span class="sxs-lookup"><span data-stu-id="2092c-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="2092c-111">Označuje, že je zadáno automatické klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2092c-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="2092c-112">Označuje, že je zadáno klíčové slovo OLE.</span><span class="sxs-lookup"><span data-stu-id="2092c-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="2092c-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="2092c-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2092c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2092c-114">Requirements</span></span>  
 <span data-ttu-id="2092c-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2092c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2092c-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="2092c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2092c-117">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2092c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2092c-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2092c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2092c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2092c-119">See also</span></span>

- [<span data-ttu-id="2092c-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="2092c-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
