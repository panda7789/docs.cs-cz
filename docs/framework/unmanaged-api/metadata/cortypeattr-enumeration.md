---
title: CorTypeAttr – výčet
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008960"
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="83e5c-102">CorTypeAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="83e5c-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="83e5c-103">Obsahuje hodnoty, které označují metadata typu.</span><span class="sxs-lookup"><span data-stu-id="83e5c-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e5c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="83e5c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83e5c-105">Members</span></span>  
  
|<span data-ttu-id="83e5c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="83e5c-106">Member</span></span>|<span data-ttu-id="83e5c-107">Description</span><span class="sxs-lookup"><span data-stu-id="83e5c-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="83e5c-108">Používá se pro informace o viditelnosti typů.</span><span class="sxs-lookup"><span data-stu-id="83e5c-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="83e5c-109">Určuje, že tento typ není ve veřejném oboru.</span><span class="sxs-lookup"><span data-stu-id="83e5c-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="83e5c-110">Určuje, že typ je ve veřejném oboru.</span><span class="sxs-lookup"><span data-stu-id="83e5c-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="83e5c-111">Určuje, že typ je vnořený s veřejnou viditelností.</span><span class="sxs-lookup"><span data-stu-id="83e5c-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="83e5c-112">Určuje, že typ je vnořený s privátní viditelností.</span><span class="sxs-lookup"><span data-stu-id="83e5c-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="83e5c-113">Určuje, že typ je vnořen s viditelností rodiny.</span><span class="sxs-lookup"><span data-stu-id="83e5c-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="83e5c-114">Určuje, že typ je vnořen s viditelností sestavení.</span><span class="sxs-lookup"><span data-stu-id="83e5c-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="83e5c-115">Určuje, že typ je vnořen s viditelností rodiny a sestavování sestavení.</span><span class="sxs-lookup"><span data-stu-id="83e5c-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="83e5c-116">Určuje, že typ je vnořen s viditelností rodin nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="83e5c-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="83e5c-117">Získá informace o rozložení pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="83e5c-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="83e5c-118">Určuje, že pole tohoto typu jsou automaticky rozložena.</span><span class="sxs-lookup"><span data-stu-id="83e5c-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="83e5c-119">Určuje, že pole tohoto typu jsou rozložena sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="83e5c-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="83e5c-120">Určuje, že rozložení pole je zadáno explicitně.</span><span class="sxs-lookup"><span data-stu-id="83e5c-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="83e5c-121">Získá sémantické informace o typu.</span><span class="sxs-lookup"><span data-stu-id="83e5c-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="83e5c-122">Určuje, že typ je třída.</span><span class="sxs-lookup"><span data-stu-id="83e5c-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="83e5c-123">Určuje, že typ je rozhraní.</span><span class="sxs-lookup"><span data-stu-id="83e5c-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="83e5c-124">Určuje, že typ je abstraktní.</span><span class="sxs-lookup"><span data-stu-id="83e5c-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="83e5c-125">Určuje, že typ nelze rozšířit.</span><span class="sxs-lookup"><span data-stu-id="83e5c-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="83e5c-126">Určuje, že název třídy je speciální.</span><span class="sxs-lookup"><span data-stu-id="83e5c-126">Specifies that the class name is special.</span></span> <span data-ttu-id="83e5c-127">Jeho název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="83e5c-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="83e5c-128">Určuje, že se typ importuje.</span><span class="sxs-lookup"><span data-stu-id="83e5c-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="83e5c-129">Určuje, že typ je serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="83e5c-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="83e5c-130">Určuje, že tento typ je prostředí Windows Runtime typ.</span><span class="sxs-lookup"><span data-stu-id="83e5c-130">Specifies that this type is a Windows Runtime type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="83e5c-131">Načte informace o tom, jak jsou řetězce kódované a naformátované.</span><span class="sxs-lookup"><span data-stu-id="83e5c-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="83e5c-132">Určuje, že tento typ interpretuje LPTSTR jako ANSI.</span><span class="sxs-lookup"><span data-stu-id="83e5c-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="83e5c-133">Určuje, že tento typ interpretuje LPTSTR jako Unicode.</span><span class="sxs-lookup"><span data-stu-id="83e5c-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="83e5c-134">Určuje, že tento typ interpretuje LPTSTR automaticky.</span><span class="sxs-lookup"><span data-stu-id="83e5c-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="83e5c-135">Určuje, že typ má nestandardní kódování, jak je uvedeno v `CustomFormatMask` .</span><span class="sxs-lookup"><span data-stu-id="83e5c-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="83e5c-136">Tuto masku použijte k získání nestandardních informací o kódování pro nativní spolupráci.</span><span class="sxs-lookup"><span data-stu-id="83e5c-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="83e5c-137">Význam hodnot těchto dvou bitů není určen.</span><span class="sxs-lookup"><span data-stu-id="83e5c-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="83e5c-138">Určuje, že typ musí být inicializován před prvním pokusem o přístup k statickému poli.</span><span class="sxs-lookup"><span data-stu-id="83e5c-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="83e5c-139">Určuje, že je typ exportován, a předávání typu.</span><span class="sxs-lookup"><span data-stu-id="83e5c-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="83e5c-140">Tento příznak a níže uvedené příznaky se používají interně modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="83e5c-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="83e5c-141">Určuje, že by měl modul CLR (Common Language Runtime) kontrolovat kódování názvu.</span><span class="sxs-lookup"><span data-stu-id="83e5c-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="83e5c-142">Určuje, že k typu je přidruženo zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="83e5c-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83e5c-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83e5c-143">Requirements</span></span>  
 <span data-ttu-id="83e5c-144">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e5c-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e5c-145">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="83e5c-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="83e5c-146">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e5c-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e5c-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="83e5c-147">See also</span></span>

- [<span data-ttu-id="83e5c-148">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="83e5c-148">Metadata Enumerations</span></span>](metadata-enumerations.md)
