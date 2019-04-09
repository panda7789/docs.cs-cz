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
ms.openlocfilehash: 66d650adb39a9c7dade0936ec671ae5a8b4aeecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170059"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="f6ace-102">CorNativeLinkType – výčet</span><span class="sxs-lookup"><span data-stu-id="f6ace-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="f6ace-103">Obsahuje hodnoty, které označují typ propojené v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="f6ace-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ace-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6ace-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f6ace-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f6ace-105">Members</span></span>  
  
|<span data-ttu-id="f6ace-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f6ace-106">Member</span></span>|<span data-ttu-id="f6ace-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ace-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="f6ace-108">Označuje, že jsou zadána žádná klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="f6ace-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="f6ace-109">Určuje, zda je zadán ANSI – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f6ace-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="f6ace-110">Určuje, zda je zadán Unicode – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="f6ace-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="f6ace-111">Určuje, zda je zadán klíčovým slovem auto.</span><span class="sxs-lookup"><span data-stu-id="f6ace-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="f6ace-112">Označuje, zda je zadán klíčovým slovem OLE.</span><span class="sxs-lookup"><span data-stu-id="f6ace-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="f6ace-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f6ace-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6ace-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6ace-114">Requirements</span></span>  
 <span data-ttu-id="f6ace-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6ace-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6ace-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6ace-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6ace-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6ace-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f6ace-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f6ace-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f6ace-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6ace-119">See also</span></span>

- [<span data-ttu-id="f6ace-120">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="f6ace-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
