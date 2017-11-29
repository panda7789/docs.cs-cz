---
title: "CorFieldAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b199764ea0fb2d02b01d7cf04d1fa8fad743109f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="b0326-102">CorFieldAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="b0326-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="b0326-103">Obsahuje hodnoty, které popisují metadata o pole.</span><span class="sxs-lookup"><span data-stu-id="b0326-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0326-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0326-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b0326-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b0326-105">Members</span></span>  
  
|<span data-ttu-id="b0326-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b0326-106">Member</span></span>|<span data-ttu-id="b0326-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b0326-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="b0326-108">Určuje informace o usnadnění.</span><span class="sxs-lookup"><span data-stu-id="b0326-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="b0326-109">Určuje, že se nemůže odkazovat pole.</span><span class="sxs-lookup"><span data-stu-id="b0326-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="b0326-110">Určuje, že je dostupný pouze pomocí jeho nadřazený typ pole.</span><span class="sxs-lookup"><span data-stu-id="b0326-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="b0326-111">Určuje, že pole je přístupné odvozené třídy v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0326-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="b0326-112">Určuje, že pole je přístupný pro všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0326-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="b0326-113">Určuje, že pole je přístupné pouze její typ a odvozených třídách.</span><span class="sxs-lookup"><span data-stu-id="b0326-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="b0326-114">Určuje, že pole je přístupný odvozené třídy a všechny typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0326-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="b0326-115">Určuje, že pole je přístupný pro všechny typy pomocí viditelnost tento obor.</span><span class="sxs-lookup"><span data-stu-id="b0326-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="b0326-116">Určuje, že je pole členem její typ a nikoli instanci členu.</span><span class="sxs-lookup"><span data-stu-id="b0326-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="b0326-117">Určuje, že pole nelze změnit po inicializaci.</span><span class="sxs-lookup"><span data-stu-id="b0326-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="b0326-118">Určuje, že hodnota pole je konstanta kompilaci.</span><span class="sxs-lookup"><span data-stu-id="b0326-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="b0326-119">Určuje, zda pole není serializovat, když jeho typ je vzdálený.</span><span class="sxs-lookup"><span data-stu-id="b0326-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="b0326-120">Určuje, že pole je speciální a, jeho název popisuje jak.</span><span class="sxs-lookup"><span data-stu-id="b0326-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="b0326-121">Určuje, že je pomocí služby PInvoke dál implementace pole.</span><span class="sxs-lookup"><span data-stu-id="b0326-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="b0326-122">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="b0326-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="b0326-123">Určuje, že běžná metadata modulu runtime jazyka interní rozhraní API měli kontrolovat kódování názvu.</span><span class="sxs-lookup"><span data-stu-id="b0326-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="b0326-124">Určuje, že pole obsahuje zařazování informace.</span><span class="sxs-lookup"><span data-stu-id="b0326-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="b0326-125">Určuje, zda pole má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b0326-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="b0326-126">Určuje, zda má pole relativní virtuální adresu.</span><span class="sxs-lookup"><span data-stu-id="b0326-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0326-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0326-127">Requirements</span></span>  
 <span data-ttu-id="b0326-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0326-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0326-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b0326-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b0326-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0326-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0326-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0326-131">See Also</span></span>  
 [<span data-ttu-id="b0326-132">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="b0326-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
