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
ms.openlocfilehash: 9d30c8fe71a0dfff7de9bb2f43b325cbb8016a23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123042"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="c9a4f-102">GUID_ManagedName – atribut</span><span class="sxs-lookup"><span data-stu-id="c9a4f-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="c9a4f-103">Definuje vlastní atribut rozhraní, který určuje název spravovaného oboru názvů pro knihovnu modelu COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="c9a4f-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9a4f-104">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9a4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9a4f-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="c9a4f-106">Název spravovaného oboru názvů pro knihovnu.</span><span class="sxs-lookup"><span data-stu-id="c9a4f-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="c9a4f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c9a4f-107">Definition</span></span>  
 <span data-ttu-id="c9a4f-108">`GUID_ManagedName` je definována v cor. h následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c9a4f-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9a4f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9a4f-109">Remarks</span></span>  
 <span data-ttu-id="c9a4f-110">Vlastní atribut rozhraní definuje metadata pro objekt v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="c9a4f-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="c9a4f-111">K načtení spravovaného názvu z atributu použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9a4f-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="c9a4f-112">Další informace naleznete v tématu [atributy rozhraní](/cpp/windows/attributes/interface-attributes) v dokumentaci Visual C++ reference.</span><span class="sxs-lookup"><span data-stu-id="c9a4f-112">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a4f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9a4f-113">Example</span></span>  
 <span data-ttu-id="c9a4f-114">Následující příklad ukazuje definici knihovny pomocí atributu `GUID_ManagedName`.</span><span class="sxs-lookup"><span data-stu-id="c9a4f-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="c9a4f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9a4f-115">Requirements</span></span>  
 <span data-ttu-id="c9a4f-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c9a4f-116">**Header:** Cor.h</span></span>
