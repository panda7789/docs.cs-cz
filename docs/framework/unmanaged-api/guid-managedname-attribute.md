---
title: "GUID_ManagedName – atribut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GUID_ManagedName
api_location: alink.dll
api_type: COM
f1_keywords: GUID_ManagedName
helpviewer_keywords: GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 116a9e38b9885f0d0a5afc8f4915b9ce2b50f1dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="guidmanagedname-attribute"></a><span data-ttu-id="bc6a5-102">GUID_ManagedName – atribut</span><span class="sxs-lookup"><span data-stu-id="bc6a5-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="bc6a5-103">Definuje rozhraní pro vlastní atribut, který určuje název spravovaného oboru názvů pro knihovny součásti object model (COM).</span><span class="sxs-lookup"><span data-stu-id="bc6a5-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc6a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc6a5-104">Syntax</span></span>  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc6a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc6a5-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="bc6a5-106">Název spravovaného obor názvů pro knihovny.</span><span class="sxs-lookup"><span data-stu-id="bc6a5-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="bc6a5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="bc6a5-107">Definition</span></span>  
 <span data-ttu-id="bc6a5-108">`GUID_ManagedName`je definováno v Cor.h následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="bc6a5-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bc6a5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc6a5-109">Remarks</span></span>  
 <span data-ttu-id="bc6a5-110">Vlastní rozhraní atribut definuje metadata pro objekt knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bc6a5-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="bc6a5-111">Použití <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> načíst spravovaný název z atributu.</span><span class="sxs-lookup"><span data-stu-id="bc6a5-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="bc6a5-112">Další informace najdete v tématu [atributy rozhraní](/cpp/windows/interface-attributes) v jazyce Visual C++ referenční dokumentace.</span><span class="sxs-lookup"><span data-stu-id="bc6a5-112">For more information, see [Interface Attributes](/cpp/windows/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6a5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc6a5-113">Example</span></span>  
 <span data-ttu-id="bc6a5-114">Následující příklad ukazuje definici knihovny pomocí `GUID_ManagedName` atribut.</span><span class="sxs-lookup"><span data-stu-id="bc6a5-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="bc6a5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc6a5-115">Requirements</span></span>  
 <span data-ttu-id="bc6a5-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc6a5-116">**Header:** Cor.h</span></span>
