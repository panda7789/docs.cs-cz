---
title: CorElementType – výčet
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: a4e9268d292004f447b30c82f1db4d0fe58404fe
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937948"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="9e495-102">CorElementType – výčet</span><span class="sxs-lookup"><span data-stu-id="9e495-102">CorElementType Enumeration</span></span>

<span data-ttu-id="9e495-103">Určuje modul CLR (Common Language Runtime) <xref:System.Type>, modifikátor typu nebo informace o typu v signatuře typu metadat.</span><span class="sxs-lookup"><span data-stu-id="9e495-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e495-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e495-104">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="9e495-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9e495-105">Members</span></span>

|<span data-ttu-id="9e495-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9e495-106">Member</span></span>|<span data-ttu-id="9e495-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9e495-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="9e495-108">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="9e495-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="9e495-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="9e495-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="9e495-110">Typ Boolean</span><span class="sxs-lookup"><span data-stu-id="9e495-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="9e495-111">Typ znaku.</span><span class="sxs-lookup"><span data-stu-id="9e495-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="9e495-112">Celé číslo se znaménkem na 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="9e495-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="9e495-113">Celé číslo s nepodepsaným 1 bajtem.</span><span class="sxs-lookup"><span data-stu-id="9e495-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="9e495-114">Celé číslo se znaménkem na 2 bajt.</span><span class="sxs-lookup"><span data-stu-id="9e495-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="9e495-115">Celé číslo bez znaménka 2-Byte.</span><span class="sxs-lookup"><span data-stu-id="9e495-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="9e495-116">Celé číslo se znaménkem o velikosti 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="9e495-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="9e495-117">Celé číslo se znaménkem a 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="9e495-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="9e495-118">Celé 8bitové číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="9e495-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="9e495-119">Celé číslo bez znaménka na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9e495-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="9e495-120">Desetinná čárka se čtyřmi bajty.</span><span class="sxs-lookup"><span data-stu-id="9e495-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="9e495-121">Plovoucí desetinná čárka (8 bajtů).</span><span class="sxs-lookup"><span data-stu-id="9e495-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="9e495-122">Typ System. String.</span><span class="sxs-lookup"><span data-stu-id="9e495-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="9e495-123">Modifikátor typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="9e495-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="9e495-124">Modifikátor typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="9e495-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="9e495-125">Modifikátor typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9e495-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="9e495-126">Modifikátor typu třídy.</span><span class="sxs-lookup"><span data-stu-id="9e495-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="9e495-127">Modifikátor typu proměnné třídy.</span><span class="sxs-lookup"><span data-stu-id="9e495-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="9e495-128">Modifikátor typu multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="9e495-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="9e495-129">Modifikátor typu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="9e495-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="9e495-130">Zadaný odkaz.</span><span class="sxs-lookup"><span data-stu-id="9e495-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="9e495-131">Velikost nativního celého čísla.</span><span class="sxs-lookup"><span data-stu-id="9e495-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="9e495-132">Velikost nativního celého čísla bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="9e495-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="9e495-133">Ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="9e495-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="9e495-134">Typ System. Object.</span><span class="sxs-lookup"><span data-stu-id="9e495-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="9e495-135">Jednorozměrné, nulový modifikátor typu pole s nižším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="9e495-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="9e495-136">Modifikátor typu proměnné metody.</span><span class="sxs-lookup"><span data-stu-id="9e495-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="9e495-137">Modifikátor vyžadovaný jazykem jazyka C.</span><span class="sxs-lookup"><span data-stu-id="9e495-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="9e495-138">Volitelný modifikátor jazyka C.</span><span class="sxs-lookup"><span data-stu-id="9e495-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="9e495-139">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="9e495-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="9e495-140">Neplatný typ.</span><span class="sxs-lookup"><span data-stu-id="9e495-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="9e495-141">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="9e495-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="9e495-142">Modifikátor typu, který je Sentinel pro seznam variabilního počtu parametrů.</span><span class="sxs-lookup"><span data-stu-id="9e495-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="9e495-143">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="9e495-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9e495-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e495-144">Remarks</span></span>

<span data-ttu-id="9e495-145">Modifikátory typu tvoří základ pro reprezentace složitějších typů.</span><span class="sxs-lookup"><span data-stu-id="9e495-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="9e495-146">Hodnota modifikátoru typu `CorElementType` se aplikuje na hodnotu, která se v signatuře typu hned za ní následuje.</span><span class="sxs-lookup"><span data-stu-id="9e495-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="9e495-147">Hodnota, která následuje za hodnotou modifikátoru typu `CorElementType`, může být `CorElementType` jednoduchá hodnota typu, token metadat nebo jiná hodnota, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9e495-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="9e495-148">Všechna čísla (*číslo*, *počet argumentů*, *token metadat*, *pořadí*, *počet*a *mez*) jsou ukládána jako komprimovaná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="9e495-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="9e495-149">Podrobnosti najdete v tématu [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) na webu ECMA.</span><span class="sxs-lookup"><span data-stu-id="9e495-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="9e495-150">Modifikátor typu</span><span class="sxs-lookup"><span data-stu-id="9e495-150">Type modifier</span></span>|<span data-ttu-id="9e495-151">Formát</span><span class="sxs-lookup"><span data-stu-id="9e495-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="9e495-152">ELEMENT_TYPE_PTR \<hodnotu `CorElementType` ></span><span class="sxs-lookup"><span data-stu-id="9e495-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="9e495-153">ELEMENT_TYPE_BYREF \<hodnotu `CorElementType` ></span><span class="sxs-lookup"><span data-stu-id="9e495-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="9e495-154">ELEMENT_TYPE_VALUETYPE \<tokenu metadat `mdTypeDef` ></span><span class="sxs-lookup"><span data-stu-id="9e495-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="9e495-155">ELEMENT_TYPE_CLASS \<tokenu metadat `mdTypeDef` ></span><span class="sxs-lookup"><span data-stu-id="9e495-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="9e495-156">Číslo \<ELEMENT_TYPE_VAR ></span><span class="sxs-lookup"><span data-stu-id="9e495-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="9e495-157">ELEMENT_TYPE_ARRAY \<`CorElementType` hodnotě > \<Rank > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="9e495-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="9e495-158">ELEMENT_TYPE_GENERICINST \<tokenu metadat `mdTypeDef` > \<počet argumentů > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="9e495-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="9e495-159">ELEMENT_TYPE_FNPTR \<kompletní signaturu funkce, včetně konvence volání ></span><span class="sxs-lookup"><span data-stu-id="9e495-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="9e495-160">ELEMENT_TYPE_SZARRAY \<hodnotu `CorElementType` ></span><span class="sxs-lookup"><span data-stu-id="9e495-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="9e495-161">Číslo \<ELEMENT_TYPE_MVAR ></span><span class="sxs-lookup"><span data-stu-id="9e495-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="9e495-162">ELEMENT_TYPE_\<`mdTypeRef` nebo `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="9e495-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="9e495-163">E_T_CMOD_OPT \<`mdTypeRef` nebo `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="9e495-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="9e495-164">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e495-164">Requirements</span></span>

<span data-ttu-id="9e495-165">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e495-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9e495-166">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9e495-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="9e495-167">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e495-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9e495-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e495-168">See also</span></span>

- [<span data-ttu-id="9e495-169">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9e495-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
