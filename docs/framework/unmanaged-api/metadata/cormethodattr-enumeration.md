---
title: CorMethodAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176992"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="00529-102">CorMethodAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="00529-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="00529-103">Obsahuje hodnoty, které popisují funkce metody.</span><span class="sxs-lookup"><span data-stu-id="00529-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00529-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00529-104">Syntax</span></span>  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="00529-105">Členové</span><span class="sxs-lookup"><span data-stu-id="00529-105">Members</span></span>  
  
|<span data-ttu-id="00529-106">Člen</span><span class="sxs-lookup"><span data-stu-id="00529-106">Member</span></span>|<span data-ttu-id="00529-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00529-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="00529-108">Určuje přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="00529-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="00529-109">Určuje, že člen se nedá odkazovat.</span><span class="sxs-lookup"><span data-stu-id="00529-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="00529-110">Určuje, že člen je přístupný pouze pomocí nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="00529-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="00529-111">Určuje, že člen je přístupný pro podtypy pouze v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="00529-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="00529-112">Určuje, zda člen accessibly kdokoli v sestavení.</span><span class="sxs-lookup"><span data-stu-id="00529-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="00529-113">Určuje, že člen je přístupný pouze podle typu a podtypy.</span><span class="sxs-lookup"><span data-stu-id="00529-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="00529-114">Určuje, že člen je přístupný z odvozených tříd a další typy v sestavení.</span><span class="sxs-lookup"><span data-stu-id="00529-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="00529-115">Určuje, že člen je přístupné pro všechny typy s přístupem k oboru.</span><span class="sxs-lookup"><span data-stu-id="00529-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="00529-116">Určuje, že člen je definovaný v rámci typu, nikoli jako člena instance.</span><span class="sxs-lookup"><span data-stu-id="00529-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="00529-117">Určuje, že metoda nemůže být přepsána.</span><span class="sxs-lookup"><span data-stu-id="00529-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="00529-118">Určuje, zda lze přepsat metodu.</span><span class="sxs-lookup"><span data-stu-id="00529-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="00529-119">Určuje, že metoda skrývá podle názvu a podpisu, nikoli pouze podle názvu.</span><span class="sxs-lookup"><span data-stu-id="00529-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="00529-120">Určuje rozložení virtuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="00529-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="00529-121">Určuje, že slotu použít pro tuto metodu v tabulce virtuální znovu použít.</span><span class="sxs-lookup"><span data-stu-id="00529-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="00529-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="00529-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="00529-123">Určuje, že metoda vždy získá nový slot v tabulce virtuální.</span><span class="sxs-lookup"><span data-stu-id="00529-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="00529-124">Určuje, že metoda se dá přepsat stejné typy, na které je viditelné.</span><span class="sxs-lookup"><span data-stu-id="00529-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="00529-125">Určuje, že metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="00529-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="00529-126">Určuje, že metoda je speciální a že jeho název popisuje jak.</span><span class="sxs-lookup"><span data-stu-id="00529-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="00529-127">Určuje, že implementace metody je dál pomocí služby PInvoke.</span><span class="sxs-lookup"><span data-stu-id="00529-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="00529-128">Určuje, že metoda je spravované metody exportovat do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="00529-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="00529-129">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="00529-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="00529-130">Určuje, že modul common language runtime by měla kontrolovat kódování název metody.</span><span class="sxs-lookup"><span data-stu-id="00529-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="00529-131">Určuje, že tato metoda má přidruženo zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="00529-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="00529-132">Určuje, že metoda volá jinou metodu obsahující zabezpečovací kód.</span><span class="sxs-lookup"><span data-stu-id="00529-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00529-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00529-133">Requirements</span></span>  
 <span data-ttu-id="00529-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00529-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00529-135">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="00529-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00529-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00529-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00529-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00529-137">See also</span></span>

- [<span data-ttu-id="00529-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="00529-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
