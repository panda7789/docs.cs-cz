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
ms.openlocfilehash: 0f946179fc31adebc8e8fc67c394e0b55a876f49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641327"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="dd151-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="dd151-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="dd151-103">Obsahuje hodnoty, které označují typ propojené v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="dd151-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd151-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd151-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dd151-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dd151-105">Members</span></span>  
  
|<span data-ttu-id="dd151-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dd151-106">Member</span></span>|<span data-ttu-id="dd151-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dd151-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="dd151-108">Označuje, že jsou zadána žádná klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="dd151-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="dd151-109">Určuje, zda je zadán ANSI – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dd151-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="dd151-110">Určuje, zda je zadán Unicode – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="dd151-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="dd151-111">Určuje, zda je zadán klíčovým slovem auto.</span><span class="sxs-lookup"><span data-stu-id="dd151-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="dd151-112">Označuje, zda je zadán klíčovým slovem OLE.</span><span class="sxs-lookup"><span data-stu-id="dd151-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="dd151-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="dd151-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd151-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd151-114">Requirements</span></span>  
 <span data-ttu-id="dd151-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd151-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd151-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd151-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd151-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd151-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd151-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd151-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd151-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd151-119">See also</span></span>
- [<span data-ttu-id="dd151-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="dd151-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
