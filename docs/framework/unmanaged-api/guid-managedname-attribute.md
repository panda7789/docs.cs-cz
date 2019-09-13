---
title: GUID_ManagedName – atribut
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d00f17a61576a50e26d3cbcf734a10ed3c03a
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895015"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="f5743-102">GUID_ManagedName – atribut</span><span class="sxs-lookup"><span data-stu-id="f5743-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="f5743-103">Definuje vlastní atribut rozhraní, který určuje název spravovaného oboru názvů pro knihovnu modelu COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="f5743-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5743-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5743-104">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5743-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5743-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="f5743-106">Název spravovaného oboru názvů pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="f5743-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="f5743-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f5743-107">Definition</span></span>  
 <span data-ttu-id="f5743-108">`GUID_ManagedName`je definována v cor. h následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f5743-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5743-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5743-109">Remarks</span></span>  
 <span data-ttu-id="f5743-110">Vlastní atribut rozhraní definuje metadata pro objekt v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="f5743-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="f5743-111">Použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> k načtení spravovaného názvu z atributu.</span><span class="sxs-lookup"><span data-stu-id="f5743-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="f5743-112">Další informace naleznete v tématu [atributy rozhraní](/cpp/windows/attributes/interface-attributes) v dokumentaci Visual C++ reference.</span><span class="sxs-lookup"><span data-stu-id="f5743-112">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5743-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5743-113">Example</span></span>  
 <span data-ttu-id="f5743-114">Následující příklad ukazuje definici knihovny pomocí `GUID_ManagedName` atributu.</span><span class="sxs-lookup"><span data-stu-id="f5743-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5743-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5743-115">Requirements</span></span>  
 <span data-ttu-id="f5743-116">**Hlaviček** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5743-116">**Header:** Cor.h</span></span>
