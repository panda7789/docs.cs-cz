---
title: CorElementType – výčet 1
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5112c3c8d5fef6efada4bffdfa575716503515e6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041353"
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="c6ca0-102">CorElementType – výčet 1</span><span class="sxs-lookup"><span data-stu-id="c6ca0-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="c6ca0-103">Určuje modul common language runtime <xref:System.Type>, modifikátor typu nebo informace o typu v signatuře typu metadat.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ca0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ca0-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="c6ca0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c6ca0-105">Members</span></span>  
  
|<span data-ttu-id="c6ca0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c6ca0-106">Member</span></span>|<span data-ttu-id="c6ca0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c6ca0-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="c6ca0-108">Interně.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="c6ca0-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="c6ca0-110">Typ Boolean</span><span class="sxs-lookup"><span data-stu-id="c6ca0-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="c6ca0-111">Typ znaku.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="c6ca0-112">1bajtový celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="c6ca0-113">1bajtový celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="c6ca0-114">2 bajty celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="c6ca0-115">2 bajty celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="c6ca0-116">4 bajty celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="c6ca0-117">Celé číslo bez znaménka na 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="c6ca0-118">8bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="c6ca0-119">8bitové celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="c6ca0-120">Bod s plovoucí desetinnou čárkou na 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="c6ca0-121">8 bajtů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="c6ca0-122">Typu System.String.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="c6ca0-123">Modifikátor typu ukazatel.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="c6ca0-124">Modifikátor typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="c6ca0-125">Modifikátor typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="c6ca0-126">Modifikátor typu třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="c6ca0-127">Typ proměnné Modifikátor třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="c6ca0-128">Modifikátor typu vícerozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="c6ca0-129">Modifikátor typu pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="c6ca0-130">Zadaný odkaz.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="c6ca0-131">Velikost nativní celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="c6ca0-132">Velikost celé číslo bez znaménka nativní.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="c6ca0-133">Ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="c6ca0-134">Typ System.Object.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="c6ca0-135">Jednorozměrná, nula dolní mez pole modifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="c6ca0-136">Metoda modifikátor typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="c6ca0-137">Jazyk C vyžaduje modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="c6ca0-138">Jazyk C volitelný modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="c6ca0-139">Interně.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="c6ca0-140">Neplatný typ.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="c6ca0-141">Interně.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="c6ca0-142">Modifikátor typu, který je sentinel seznam proměnný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="c6ca0-143">Interně.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6ca0-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ca0-144">Remarks</span></span>  
 <span data-ttu-id="c6ca0-145">Modifikátory typu jsou základem představující složitější typy.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="c6ca0-146">A `CorElementType` hodnota modifikátor typu je použité pro hodnotu, která bezprostředně následuje v signatuře typu.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="c6ca0-147">Hodnota, která následuje `CorElementType` může být hodnota modifikátor typu `CorElementType` hodnota jednoduchého typu, token metadat nebo jiná hodnota, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6ca0-148">Všechna čísla (*číslo*, *argumentů Count*, *tokenu metadat*, *pořadí*, *počet*a *vázán*) jsou uloženy jako komprimovaný celá čísla.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="c6ca0-149">Zobrazit [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) na webu ECMA podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c6ca0-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="c6ca0-150">Modifikátor typu</span><span class="sxs-lookup"><span data-stu-id="c6ca0-150">Type modifier</span></span>|<span data-ttu-id="c6ca0-151">Formát</span><span class="sxs-lookup"><span data-stu-id="c6ca0-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="c6ca0-152">Typ ELEMENT_TYPE_PTR < `CorElementType` hodnotu ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="c6ca0-153">ELEMENT_TYPE_BYREF < `CorElementType` hodnotu ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="c6ca0-154">Typ ELEMENT_TYPE_VALUETYPE, který < `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="c6ca0-155">Za řetězcem ELEMENT_TYPE_CLASS < `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="c6ca0-156">ELEMENT_TYPE_VAR \<číslo ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="c6ca0-157">ELEMENT_TYPE_ARRAY < `CorElementType` hodnota > \<pořadí > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="c6ca0-158">ELEMENT_TYPE_GENERICINST < `mdTypeDef` tokenu metadat > \<argumentů Count > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="c6ca0-159">Typ ELEMENT_TYPE_FNPTR \<úplný podpis pro funkci, včetně konvence volání ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="c6ca0-160">ELEMENT_TYPE_SZARRAY < `CorElementType` hodnotu ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="c6ca0-161">ELEMENT_TYPE_MVAR \<číslo ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="c6ca0-162">Typ ELEMENT_TYPE_ < `mdTypeRef` nebo `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="c6ca0-163">E_T_CMOD_OPT < `mdTypeRef` nebo `mdTypeDef` tokenu metadat ></span><span class="sxs-lookup"><span data-stu-id="c6ca0-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6ca0-164">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6ca0-164">Requirements</span></span>  
 <span data-ttu-id="c6ca0-165">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6ca0-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6ca0-166">**Záhlaví:** Comimage_flags</span><span class="sxs-lookup"><span data-stu-id="c6ca0-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c6ca0-167">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6ca0-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ca0-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6ca0-168">See Also</span></span>  
 [<span data-ttu-id="c6ca0-169">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c6ca0-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
