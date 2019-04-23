---
title: CorFieldAttr – výčet
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 432e202eb8db105e8d56d3d36cdc8001bac5320c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182374"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="e0ff5-102">CorFieldAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="e0ff5-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="e0ff5-103">Obsahuje hodnoty, které popisují metadata o pole.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ff5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0ff5-104">Syntax</span></span>  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="e0ff5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e0ff5-105">Members</span></span>  
  
|<span data-ttu-id="e0ff5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e0ff5-106">Member</span></span>|<span data-ttu-id="e0ff5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e0ff5-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="e0ff5-108">Určuje informace o usnadnění.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="e0ff5-109">Určuje, že pole se nedá odkazovat.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="e0ff5-110">Určuje, že pole je přístupná jenom pro jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="e0ff5-111">Určuje, že pole je přístupné z odvozených tříd v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="e0ff5-112">Určuje, že pole je přístupné pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="e0ff5-113">Určuje, že pole je přístupná jenom pro její typ a odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="e0ff5-114">Určuje, že pole je přístupný z odvozených tříd a všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="e0ff5-115">Určuje, že pole je přístupné pro všechny typy s viditelnost tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="e0ff5-116">Určuje, že pole je členem jeho typu, nikoli člena instance.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="e0ff5-117">Určuje, že pole nelze změnit po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="e0ff5-118">Určuje, že hodnota pole je konstantu kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="e0ff5-119">Určuje, že pole není serializovat, když je její typ je vzdálený.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="e0ff5-120">Určuje, že pole je speciální a který odpovídá názvu jak.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="e0ff5-121">Určuje, že implementace pole je dál prostřednictvím PInvoke.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="e0ff5-122">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="e0ff5-123">Určuje, že common language runtime metadata interních rozhraních API by měla kontrolovat kódování názvu.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="e0ff5-124">Určuje, zda pole obsahuje zařazovací informace.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="e0ff5-125">Určuje, že pole má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="e0ff5-126">Určuje, že pole má relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="e0ff5-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0ff5-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0ff5-127">Requirements</span></span>  
 <span data-ttu-id="e0ff5-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0ff5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0ff5-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e0ff5-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e0ff5-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0ff5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ff5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0ff5-131">See also</span></span>

- [<span data-ttu-id="e0ff5-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="e0ff5-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
