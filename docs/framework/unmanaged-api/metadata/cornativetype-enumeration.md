---
title: CorNativeType – výčet
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: ef4788891e91608a394482319a89b8b0d258449f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436513"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="f4045-102">CorNativeType – výčet</span><span class="sxs-lookup"><span data-stu-id="f4045-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="f4045-103">Obsahuje hodnoty, které popisují nativní nespravované typy.</span><span class="sxs-lookup"><span data-stu-id="f4045-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4045-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4045-104">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="f4045-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f4045-105">Members</span></span>  
  
|<span data-ttu-id="f4045-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f4045-106">Member</span></span>|<span data-ttu-id="f4045-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f4045-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="f4045-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="f4045-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="f4045-110">Kladná logická hodnota o velikosti 4 bajty, kde TRUE je nenulová a hodnota FALSE je nula.</span><span class="sxs-lookup"><span data-stu-id="f4045-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="f4045-111">8bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="f4045-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="f4045-112">16bitová celočíselná hodnota bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="f4045-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="f4045-113">16bitová celočíselná hodnota se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="f4045-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="f4045-114">16bitová celočíselná hodnota bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="f4045-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="f4045-115">Podepsaná hodnota se znaménkem 32.</span><span class="sxs-lookup"><span data-stu-id="f4045-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="f4045-116">Celočíselná hodnota bez znaménka 32-bit.</span><span class="sxs-lookup"><span data-stu-id="f4045-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="f4045-117">Podepsaná hodnota se znaménkem 64.</span><span class="sxs-lookup"><span data-stu-id="f4045-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="f4045-118">Celočíselná hodnota bez znaménka 64-bit.</span><span class="sxs-lookup"><span data-stu-id="f4045-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="f4045-119">Číselná hodnota s plovoucí desetinnou čárkou a 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="f4045-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="f4045-120">Číselná hodnota s plovoucí desetinnou čárkou o velikosti 8 bajtů.</span><span class="sxs-lookup"><span data-stu-id="f4045-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="f4045-121">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="f4045-122">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="f4045-123">Číselný typ COM, který odpovídá spravovanému typu <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="f4045-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="f4045-124">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="f4045-125">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="f4045-126">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="f4045-127">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="f4045-128">Hodnota řetězce typem LPStr.</span><span class="sxs-lookup"><span data-stu-id="f4045-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="f4045-129">Hodnota řetězce LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="f4045-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="f4045-130">Hodnota řetězce LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="f4045-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="f4045-131">Pevná, systémem definovaná řetězcová hodnota.</span><span class="sxs-lookup"><span data-stu-id="f4045-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="f4045-132">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="f4045-133">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="f4045-134">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="f4045-135">Hodnota nativní struktury.</span><span class="sxs-lookup"><span data-stu-id="f4045-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="f4045-136">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="f4045-137">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="f4045-138">Hodnota pole s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="f4045-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="f4045-139">Nativní 16bitové celočíselné hodnoty se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="f4045-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="f4045-140">Nativní 16bitová hodnota unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="f4045-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="f4045-141">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f4045-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="f4045-142">Použijte NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="f4045-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="f4045-143">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="f4045-144">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="f4045-145">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="f4045-146">V závislosti na platformě vyberte BSTR nebo ANSIBSTR.</span><span class="sxs-lookup"><span data-stu-id="f4045-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="f4045-147">Logická hodnota 2 bajtů, kde TRUE je-1 a FALSE je nula.</span><span class="sxs-lookup"><span data-stu-id="f4045-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="f4045-148">Ukazatel na funkci.</span><span class="sxs-lookup"><span data-stu-id="f4045-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="f4045-149">Odkaz na jakýkoliv nativní typ.</span><span class="sxs-lookup"><span data-stu-id="f4045-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="f4045-150">Odkaz na pole se členy nespecifikovaného typu.</span><span class="sxs-lookup"><span data-stu-id="f4045-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="f4045-151">Ne32ý celočíselný ukazatel na strukturu.</span><span class="sxs-lookup"><span data-stu-id="f4045-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="f4045-152">Vlastní nativní typ zařazovacího modulu.</span><span class="sxs-lookup"><span data-stu-id="f4045-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="f4045-153">Musí následovat řetězec v následujícím formátu: "název nativního typu/0Custom zařazovacího typu/0Optional soubor cookie/0" nebo "{Native GUID} název typu/0Optional soubor cookie/0"</span><span class="sxs-lookup"><span data-stu-id="f4045-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="f4045-154">Zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="f4045-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="f4045-155">ELEMENT_TYPE_I4 tento typ mapuje na VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f4045-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="f4045-156">Nativní typ `IInspectable`.</span><span class="sxs-lookup"><span data-stu-id="f4045-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="f4045-157">Nativní `HString`.</span><span class="sxs-lookup"><span data-stu-id="f4045-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="f4045-158">Neplatná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f4045-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4045-159">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4045-159">Requirements</span></span>  
 <span data-ttu-id="f4045-160">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4045-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4045-161">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f4045-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f4045-162">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4045-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4045-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4045-163">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="f4045-164">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f4045-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
