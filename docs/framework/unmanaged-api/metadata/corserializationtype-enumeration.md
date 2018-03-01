---
title: "CorSerializationType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorSerializationType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSerializationType
helpviewer_keywords:
- CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="966e5-102">CorSerializationType – výčet</span><span class="sxs-lookup"><span data-stu-id="966e5-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="966e5-103">Určuje, jak modul common language runtime serializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="966e5-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="966e5-104">Syntax</span></span>  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="966e5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="966e5-105">Members</span></span>  
  
|<span data-ttu-id="966e5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="966e5-106">Member</span></span>|<span data-ttu-id="966e5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="966e5-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="966e5-108">Serializace objektu není definován.</span><span class="sxs-lookup"><span data-stu-id="966e5-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="966e5-109">Objekt serializován jako typem logická hodnota</span><span class="sxs-lookup"><span data-stu-id="966e5-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="966e5-110">Objekt serializován jako typ znak.</span><span class="sxs-lookup"><span data-stu-id="966e5-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="966e5-111">Objekt serializován jako 1bajtový znaménkem.</span><span class="sxs-lookup"><span data-stu-id="966e5-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="966e5-112">Objekt serializován jako celé číslo bez znaménka 1bajtový.</span><span class="sxs-lookup"><span data-stu-id="966e5-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="966e5-113">Objekt serializován jako 2bajtová znaménkem.</span><span class="sxs-lookup"><span data-stu-id="966e5-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="966e5-114">Objekt serializován jako celé číslo bez znaménka 2bajtová.</span><span class="sxs-lookup"><span data-stu-id="966e5-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="966e5-115">Objekt serializován jako 4bajtový znaménkem.</span><span class="sxs-lookup"><span data-stu-id="966e5-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="966e5-116">Objekt serializován jako celé číslo bez znaménka 4bajtový.</span><span class="sxs-lookup"><span data-stu-id="966e5-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="966e5-117">Objekt serializován jako znaménkem 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="966e5-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="966e5-118">Objekt serializován jako celé číslo bez znaménka 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="966e5-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="966e5-119">Objekt serializován jako 4bajtový plovoucí desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="966e5-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="966e5-120">Objekt serializován jako plovoucí desetinné čárky 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="966e5-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="966e5-121">Objekt serializován jako typ System.String.</span><span class="sxs-lookup"><span data-stu-id="966e5-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="966e5-122">Objekt serializován jako jednorozměrná, nulové dolní mez pole.</span><span class="sxs-lookup"><span data-stu-id="966e5-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="966e5-123">Objekt serializován jako obecného typu.</span><span class="sxs-lookup"><span data-stu-id="966e5-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="966e5-124">Objekt serializován jako objekt s příznakem.</span><span class="sxs-lookup"><span data-stu-id="966e5-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="966e5-125">Objekt serializován jako pole.</span><span class="sxs-lookup"><span data-stu-id="966e5-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="966e5-126">Objekt serializován jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="966e5-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="966e5-127">Objekt serializován jako Výčtový objekt.</span><span class="sxs-lookup"><span data-stu-id="966e5-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="966e5-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="966e5-128">Requirements</span></span>  
 <span data-ttu-id="966e5-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="966e5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="966e5-130">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="966e5-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="966e5-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="966e5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966e5-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="966e5-132">See Also</span></span>  
 [<span data-ttu-id="966e5-133">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="966e5-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
