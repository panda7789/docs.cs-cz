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
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007868"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="8feea-102">CorElementType – výčet</span><span class="sxs-lookup"><span data-stu-id="8feea-102">CorElementType Enumeration</span></span>

<span data-ttu-id="8feea-103">Určuje modul CLR (Common Language Runtime) <xref:System.Type> , modifikátor typu nebo informace o typu v signatuře typu metadat.</span><span class="sxs-lookup"><span data-stu-id="8feea-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="8feea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8feea-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="8feea-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8feea-105">Members</span></span>

|<span data-ttu-id="8feea-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8feea-106">Member</span></span>|<span data-ttu-id="8feea-107">Description</span><span class="sxs-lookup"><span data-stu-id="8feea-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="8feea-108">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="8feea-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="8feea-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="8feea-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="8feea-110">Typ Boolean</span><span class="sxs-lookup"><span data-stu-id="8feea-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="8feea-111">Typ znaku.</span><span class="sxs-lookup"><span data-stu-id="8feea-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="8feea-112">Celé číslo se znaménkem na 1 bajt.</span><span class="sxs-lookup"><span data-stu-id="8feea-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="8feea-113">Celé číslo s nepodepsaným 1 bajtem.</span><span class="sxs-lookup"><span data-stu-id="8feea-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="8feea-114">Celé číslo se znaménkem na 2 bajt.</span><span class="sxs-lookup"><span data-stu-id="8feea-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="8feea-115">Celé číslo bez znaménka 2-Byte.</span><span class="sxs-lookup"><span data-stu-id="8feea-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="8feea-116">Celé číslo se znaménkem o velikosti 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="8feea-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="8feea-117">Celé číslo se znaménkem a 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="8feea-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="8feea-118">Celé 8bitové číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="8feea-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="8feea-119">Celé číslo bez znaménka na 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="8feea-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="8feea-120">Desetinná čárka se čtyřmi bajty.</span><span class="sxs-lookup"><span data-stu-id="8feea-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="8feea-121">Plovoucí desetinná čárka (8 bajtů).</span><span class="sxs-lookup"><span data-stu-id="8feea-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="8feea-122">Typ System. String.</span><span class="sxs-lookup"><span data-stu-id="8feea-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="8feea-123">Modifikátor typu ukazatele.</span><span class="sxs-lookup"><span data-stu-id="8feea-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="8feea-124">Modifikátor typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="8feea-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="8feea-125">Modifikátor typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8feea-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="8feea-126">Modifikátor typu třídy.</span><span class="sxs-lookup"><span data-stu-id="8feea-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="8feea-127">Modifikátor typu proměnné třídy.</span><span class="sxs-lookup"><span data-stu-id="8feea-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="8feea-128">Modifikátor typu multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="8feea-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="8feea-129">Modifikátor typu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="8feea-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="8feea-130">Zadaný odkaz.</span><span class="sxs-lookup"><span data-stu-id="8feea-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="8feea-131">Velikost nativního celého čísla.</span><span class="sxs-lookup"><span data-stu-id="8feea-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="8feea-132">Velikost nativního celého čísla bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="8feea-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="8feea-133">Ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="8feea-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="8feea-134">Typ System. Object.</span><span class="sxs-lookup"><span data-stu-id="8feea-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="8feea-135">Jednorozměrné, nulový modifikátor typu pole s nižším rozsahem.</span><span class="sxs-lookup"><span data-stu-id="8feea-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="8feea-136">Modifikátor typu proměnné metody.</span><span class="sxs-lookup"><span data-stu-id="8feea-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="8feea-137">Modifikátor vyžadovaný jazykem jazyka C.</span><span class="sxs-lookup"><span data-stu-id="8feea-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="8feea-138">Volitelný modifikátor jazyka C.</span><span class="sxs-lookup"><span data-stu-id="8feea-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="8feea-139">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="8feea-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="8feea-140">Neplatný typ.</span><span class="sxs-lookup"><span data-stu-id="8feea-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="8feea-141">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="8feea-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="8feea-142">Modifikátor typu, který je Sentinel pro seznam variabilního počtu parametrů.</span><span class="sxs-lookup"><span data-stu-id="8feea-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="8feea-143">Používá se interně.</span><span class="sxs-lookup"><span data-stu-id="8feea-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8feea-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8feea-144">Remarks</span></span>

<span data-ttu-id="8feea-145">Modifikátory typu tvoří základ pro reprezentace složitějších typů.</span><span class="sxs-lookup"><span data-stu-id="8feea-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="8feea-146">`CorElementType`Hodnota modifikátoru typu se aplikuje na hodnotu, která se na Signature typu hned doplní.</span><span class="sxs-lookup"><span data-stu-id="8feea-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="8feea-147">Hodnota, která následuje jako `CorElementType` hodnota modifikátoru typu, může být `CorElementType` jednoduchá hodnota typu, token metadat nebo jiná hodnota, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="8feea-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="8feea-148">Všechna čísla (*číslo*, *počet argumentů*, *token metadat*, *pořadí*, *počet*a *mez*) jsou ukládána jako komprimovaná celá čísla.</span><span class="sxs-lookup"><span data-stu-id="8feea-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="8feea-149">Podrobnosti najdete v tématu [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) na webu ECMA.</span><span class="sxs-lookup"><span data-stu-id="8feea-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="8feea-150">Modifikátor typu</span><span class="sxs-lookup"><span data-stu-id="8feea-150">Type modifier</span></span>|<span data-ttu-id="8feea-151">Formát</span><span class="sxs-lookup"><span data-stu-id="8feea-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="8feea-152">ELEMENT_TYPE_PTR\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="8feea-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="8feea-153">ELEMENT_TYPE_BYREF\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="8feea-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="8feea-154">ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="8feea-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="8feea-155">ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="8feea-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="8feea-156">ELEMENT_TYPE_VAR\<number></span><span class="sxs-lookup"><span data-stu-id="8feea-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="8feea-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="8feea-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="8feea-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ...\<argN></span><span class="sxs-lookup"><span data-stu-id="8feea-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="8feea-159">ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="8feea-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="8feea-160">ELEMENT_TYPE_SZARRAY\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="8feea-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="8feea-161">ELEMENT_TYPE_MVAR\<number></span><span class="sxs-lookup"><span data-stu-id="8feea-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="8feea-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="8feea-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="8feea-163">E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="8feea-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="8feea-164">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8feea-164">Requirements</span></span>

<span data-ttu-id="8feea-165">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8feea-165">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8feea-166">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8feea-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="8feea-167">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8feea-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8feea-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="8feea-168">See also</span></span>

- [<span data-ttu-id="8feea-169">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8feea-169">Metadata Enumerations</span></span>](metadata-enumerations.md)
