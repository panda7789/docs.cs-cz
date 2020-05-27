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
ms.openlocfilehash: dea69e18fc517eddddc5b99950a6f3b16ee3e426
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007400"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="29121-102">CorFieldAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="29121-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="29121-103">Obsahuje hodnoty, které popisují metadata k poli.</span><span class="sxs-lookup"><span data-stu-id="29121-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29121-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="29121-105">Členové</span><span class="sxs-lookup"><span data-stu-id="29121-105">Members</span></span>  
  
|<span data-ttu-id="29121-106">Člen</span><span class="sxs-lookup"><span data-stu-id="29121-106">Member</span></span>|<span data-ttu-id="29121-107">Description</span><span class="sxs-lookup"><span data-stu-id="29121-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="29121-108">Určuje informace o usnadnění.</span><span class="sxs-lookup"><span data-stu-id="29121-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="29121-109">Určuje, že na pole se nedá odkazovat.</span><span class="sxs-lookup"><span data-stu-id="29121-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="29121-110">Určuje, že pole je přístupné pouze pomocí jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="29121-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="29121-111">Určuje, že pole je přístupné odvozenými třídami v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="29121-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="29121-112">Určuje, že pole je přístupné pro všechny typy v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="29121-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="29121-113">Určuje, že pole je přístupné pouze pomocí jeho typu a odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="29121-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="29121-114">Určuje, že pole je přístupné odvozenými třídami a všemi typy v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="29121-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="29121-115">Určuje, že pole je přístupné pro všechny typy s viditelností tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="29121-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="29121-116">Určuje, že pole je členem jeho typu, nikoli členem instance.</span><span class="sxs-lookup"><span data-stu-id="29121-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="29121-117">Určuje, že pole nelze po inicializaci změnit.</span><span class="sxs-lookup"><span data-stu-id="29121-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="29121-118">Určuje, že hodnota pole je konstanta při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="29121-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="29121-119">Určuje, že pole není serializováno, pokud je jeho typ vzdáleně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="29121-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="29121-120">Určuje, že pole je zvláštní a že jeho název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="29121-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="29121-121">Určuje, že implementace pole je předána pomocí PInvoke.</span><span class="sxs-lookup"><span data-stu-id="29121-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="29121-122">Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="29121-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="29121-123">Určuje, že vnitřní rozhraní API pro Common Language Runtime metadata by měla kontrolovat kódování názvu.</span><span class="sxs-lookup"><span data-stu-id="29121-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="29121-124">Určuje, že pole obsahuje informace o zařazování.</span><span class="sxs-lookup"><span data-stu-id="29121-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="29121-125">Určuje, že pole má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="29121-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="29121-126">Určuje, že pole má relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="29121-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29121-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29121-127">Requirements</span></span>  
 <span data-ttu-id="29121-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29121-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29121-129">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="29121-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="29121-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29121-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29121-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="29121-131">See also</span></span>

- [<span data-ttu-id="29121-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="29121-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
