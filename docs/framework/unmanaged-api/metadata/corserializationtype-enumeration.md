---
title: CorSerializationType – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: 064374285216e9fb054b299937087f1ca7c351a4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432869"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="65d20-102">CorSerializationType – výčet</span><span class="sxs-lookup"><span data-stu-id="65d20-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="65d20-103">Určuje, jak je objekt serializován modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="65d20-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d20-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="65d20-105">Members</span><span class="sxs-lookup"><span data-stu-id="65d20-105">Members</span></span>  
  
|<span data-ttu-id="65d20-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65d20-106">Member</span></span>|<span data-ttu-id="65d20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65d20-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="65d20-108">Serializace objektu není definována.</span><span class="sxs-lookup"><span data-stu-id="65d20-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="65d20-109">Objekt je serializován jako typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="65d20-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="65d20-110">Objekt je serializován jako typ znaku.</span><span class="sxs-lookup"><span data-stu-id="65d20-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="65d20-111">Objekt je serializován jako celé číslo se znaménkem na 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="65d20-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="65d20-112">Objekt je serializován jako celé číslo s nepodepsaným 1 bajtem.</span><span class="sxs-lookup"><span data-stu-id="65d20-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="65d20-113">Objekt je serializován jako celé číslo se znaménkem na dvou bajtech.</span><span class="sxs-lookup"><span data-stu-id="65d20-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="65d20-114">Objekt je serializován jako celé číslo bez znaménka 2 bajt.</span><span class="sxs-lookup"><span data-stu-id="65d20-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="65d20-115">Objekt je serializován jako celé číslo se znaménkem na 4 bajt.</span><span class="sxs-lookup"><span data-stu-id="65d20-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="65d20-116">Objekt je serializován jako celé číslo bez znaménka 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="65d20-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="65d20-117">Objekt je serializován jako přihlášené celé číslo se znaménkem na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="65d20-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="65d20-118">Objekt je serializován jako celé číslo bez znaménka na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="65d20-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="65d20-119">Objekt je serializován jako plovoucí desetinná čárka (4 bajt).</span><span class="sxs-lookup"><span data-stu-id="65d20-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="65d20-120">Objekt je serializován jako plovoucí desetinná čárka (8 bajtů).</span><span class="sxs-lookup"><span data-stu-id="65d20-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="65d20-121">Objekt je serializován jako typ System. String.</span><span class="sxs-lookup"><span data-stu-id="65d20-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="65d20-122">Objekt je serializován jako jednorozměrné, nulové pole s nižším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="65d20-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="65d20-123">Objekt je serializován jako obecný typ.</span><span class="sxs-lookup"><span data-stu-id="65d20-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="65d20-124">Objekt je serializován jako objekt s příznakem.</span><span class="sxs-lookup"><span data-stu-id="65d20-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="65d20-125">Objekt je serializován jako pole.</span><span class="sxs-lookup"><span data-stu-id="65d20-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="65d20-126">Objekt je serializován jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65d20-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="65d20-127">Objekt je serializován jako výčet.</span><span class="sxs-lookup"><span data-stu-id="65d20-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65d20-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65d20-128">Requirements</span></span>  
 <span data-ttu-id="65d20-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d20-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d20-130">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="65d20-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="65d20-131">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d20-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d20-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65d20-132">See also</span></span>

- [<span data-ttu-id="65d20-133">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="65d20-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
