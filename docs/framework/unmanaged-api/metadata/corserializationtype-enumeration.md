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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b1f6be2dac6bc7566852791ac22e495949521c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992638"
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="44251-102">CorSerializationType – výčet</span><span class="sxs-lookup"><span data-stu-id="44251-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="44251-103">Určuje, jak je objekt serializován modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="44251-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44251-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="44251-105">Členové</span><span class="sxs-lookup"><span data-stu-id="44251-105">Members</span></span>  
  
|<span data-ttu-id="44251-106">Člen</span><span class="sxs-lookup"><span data-stu-id="44251-106">Member</span></span>|<span data-ttu-id="44251-107">Popis</span><span class="sxs-lookup"><span data-stu-id="44251-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="44251-108">Serializace objektu není definováno.</span><span class="sxs-lookup"><span data-stu-id="44251-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="44251-109">Objekt serializován jako typ Boolean</span><span class="sxs-lookup"><span data-stu-id="44251-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="44251-110">Objekt serializován jako typ znaku.</span><span class="sxs-lookup"><span data-stu-id="44251-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="44251-111">Objekt serializován jako celé číslo se znaménkem 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="44251-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="44251-112">Objekt serializován jako celé číslo bez znaménka 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="44251-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="44251-113">Objekt serializován jako celé číslo se znaménkem 2 bajtů.</span><span class="sxs-lookup"><span data-stu-id="44251-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="44251-114">Objekt serializován jako celé číslo bez znaménka 2 bajtů.</span><span class="sxs-lookup"><span data-stu-id="44251-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="44251-115">Objekt serializován jako celé číslo se znaménkem na 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="44251-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="44251-116">Objekt serializován jako celé číslo bez znaménka na 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="44251-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="44251-117">Objekt serializován jako celé číslo se znaménkem 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="44251-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="44251-118">Objekt serializován jako 8bitové celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="44251-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="44251-119">Objekt serializován jako plovoucí desetinnou čárkou na 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="44251-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="44251-120">Objekt serializován jako plovoucí desetinnou čárkou 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="44251-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="44251-121">Objekt serializován jako typu System.String.</span><span class="sxs-lookup"><span data-stu-id="44251-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="44251-122">Objekt serializován jako jednorozměrné, nula dolní mez pole.</span><span class="sxs-lookup"><span data-stu-id="44251-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="44251-123">Objekt serializován jako obecného typu.</span><span class="sxs-lookup"><span data-stu-id="44251-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="44251-124">Objekt serializován jako objekt příznakem.</span><span class="sxs-lookup"><span data-stu-id="44251-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="44251-125">Objekt serializován jako pole.</span><span class="sxs-lookup"><span data-stu-id="44251-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="44251-126">Objekt serializován jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="44251-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="44251-127">Objekt serializován jako výčet.</span><span class="sxs-lookup"><span data-stu-id="44251-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44251-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44251-128">Requirements</span></span>  
 <span data-ttu-id="44251-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44251-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44251-130">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="44251-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="44251-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44251-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44251-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44251-132">See also</span></span>

- [<span data-ttu-id="44251-133">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="44251-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
