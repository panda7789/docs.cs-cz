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
ms.openlocfilehash: 718e41e16c07265d8a36b8f6124d99cd3490f7be
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436625"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="d4669-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="d4669-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="d4669-103">Poskytuje hodnoty, které indikují typ propojený v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="d4669-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4669-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4669-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d4669-105">Members</span><span class="sxs-lookup"><span data-stu-id="d4669-105">Members</span></span>  
  
|<span data-ttu-id="d4669-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d4669-106">Member</span></span>|<span data-ttu-id="d4669-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d4669-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="d4669-108">Označuje, že není zadáno žádné klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d4669-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="d4669-109">Indikuje, že je zadané klíčové slovo ANSI.</span><span class="sxs-lookup"><span data-stu-id="d4669-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="d4669-110">Indikuje, že je zadané klíčové slovo Unicode.</span><span class="sxs-lookup"><span data-stu-id="d4669-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="d4669-111">Indikuje, že je zadané klíčové slovo auto.</span><span class="sxs-lookup"><span data-stu-id="d4669-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="d4669-112">Indikuje, že je zadané klíčové slovo OLE.</span><span class="sxs-lookup"><span data-stu-id="d4669-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="d4669-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="d4669-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4669-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4669-114">Requirements</span></span>  
 <span data-ttu-id="d4669-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4669-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4669-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4669-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4669-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4669-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4669-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4669-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4669-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4669-119">See also</span></span>

- [<span data-ttu-id="d4669-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d4669-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
