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
ms.openlocfilehash: 0ce84e1545523302cd47e60b9f047bc470e6bf0f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443626"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="077c8-102">CorElementType – výčet</span><span class="sxs-lookup"><span data-stu-id="077c8-102">CorElementType Enumeration</span></span>

<span data-ttu-id="077c8-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span><span class="sxs-lookup"><span data-stu-id="077c8-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="077c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="077c8-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="077c8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="077c8-105">Members</span></span>

|<span data-ttu-id="077c8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="077c8-106">Member</span></span>|<span data-ttu-id="077c8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="077c8-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="077c8-108">Used internally.</span><span class="sxs-lookup"><span data-stu-id="077c8-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="077c8-109">A void type.</span><span class="sxs-lookup"><span data-stu-id="077c8-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="077c8-110">A Boolean type</span><span class="sxs-lookup"><span data-stu-id="077c8-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="077c8-111">A character type.</span><span class="sxs-lookup"><span data-stu-id="077c8-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="077c8-112">A signed 1-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="077c8-113">An unsigned 1-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="077c8-114">A signed 2-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="077c8-115">An unsigned 2-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="077c8-116">A signed 4-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="077c8-117">An unsigned 4-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="077c8-118">A signed 8-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="077c8-119">An unsigned 8-byte integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="077c8-120">A 4-byte floating point.</span><span class="sxs-lookup"><span data-stu-id="077c8-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="077c8-121">An 8-byte floating point.</span><span class="sxs-lookup"><span data-stu-id="077c8-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="077c8-122">A System.String type.</span><span class="sxs-lookup"><span data-stu-id="077c8-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="077c8-123">A pointer type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="077c8-124">A reference type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="077c8-125">A value type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="077c8-126">A class type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="077c8-127">A class variable type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="077c8-128">A multi-dimensional array type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="077c8-129">A type modifier for generic types.</span><span class="sxs-lookup"><span data-stu-id="077c8-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="077c8-130">A typed reference.</span><span class="sxs-lookup"><span data-stu-id="077c8-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="077c8-131">Size of a native integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="077c8-132">Size of an unsigned native integer.</span><span class="sxs-lookup"><span data-stu-id="077c8-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="077c8-133">A pointer to a function.</span><span class="sxs-lookup"><span data-stu-id="077c8-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="077c8-134">A System.Object type.</span><span class="sxs-lookup"><span data-stu-id="077c8-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="077c8-135">A single-dimensional, zero lower-bound array type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="077c8-136">A method variable type modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="077c8-137">A C language required modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="077c8-138">A C language optional modifier.</span><span class="sxs-lookup"><span data-stu-id="077c8-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="077c8-139">Used internally.</span><span class="sxs-lookup"><span data-stu-id="077c8-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="077c8-140">An invalid type.</span><span class="sxs-lookup"><span data-stu-id="077c8-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="077c8-141">Used internally.</span><span class="sxs-lookup"><span data-stu-id="077c8-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="077c8-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span><span class="sxs-lookup"><span data-stu-id="077c8-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="077c8-143">Used internally.</span><span class="sxs-lookup"><span data-stu-id="077c8-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="077c8-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="077c8-144">Remarks</span></span>

<span data-ttu-id="077c8-145">The type modifiers form the basis for representing more complex types.</span><span class="sxs-lookup"><span data-stu-id="077c8-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="077c8-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span><span class="sxs-lookup"><span data-stu-id="077c8-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="077c8-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span><span class="sxs-lookup"><span data-stu-id="077c8-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="077c8-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span><span class="sxs-lookup"><span data-stu-id="077c8-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="077c8-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span><span class="sxs-lookup"><span data-stu-id="077c8-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="077c8-150">Type modifier</span><span class="sxs-lookup"><span data-stu-id="077c8-150">Type modifier</span></span>|<span data-ttu-id="077c8-151">Formát</span><span class="sxs-lookup"><span data-stu-id="077c8-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="077c8-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="077c8-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="077c8-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="077c8-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="077c8-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="077c8-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="077c8-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="077c8-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="077c8-156">ELEMENT_TYPE_VAR \<number></span><span class="sxs-lookup"><span data-stu-id="077c8-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="077c8-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span><span class="sxs-lookup"><span data-stu-id="077c8-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="077c8-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span><span class="sxs-lookup"><span data-stu-id="077c8-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="077c8-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="077c8-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="077c8-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="077c8-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="077c8-161">ELEMENT_TYPE_MVAR \<number></span><span class="sxs-lookup"><span data-stu-id="077c8-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="077c8-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="077c8-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="077c8-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="077c8-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="077c8-164">Požadavky</span><span class="sxs-lookup"><span data-stu-id="077c8-164">Requirements</span></span>

<span data-ttu-id="077c8-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="077c8-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="077c8-166">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="077c8-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="077c8-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="077c8-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="077c8-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="077c8-168">See also</span></span>

- [<span data-ttu-id="077c8-169">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="077c8-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
