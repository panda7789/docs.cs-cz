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
ms.openlocfilehash: 3bae50f695de81856d4fddcb2af3d1188d896642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName – atribut
Definuje rozhraní pro vlastní atribut, který určuje název spravovaného oboru názvů pro knihovny součásti object model (COM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Název spravovaného obor názvů pro knihovny.  
  
## <a name="definition"></a>Definice  
 `GUID_ManagedName` je definováno v Cor.h následujícím způsobem:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Poznámky  
 Vlastní rozhraní atribut definuje metadata pro objekt knihovny typů.  
  
 Použití <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> načíst spravovaný název z atributu.  
  
 Další informace najdete v tématu [atributy rozhraní](/cpp/windows/interface-attributes) v jazyce Visual C++ referenční dokumentace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici knihovny pomocí `GUID_ManagedName` atribut.  
  
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
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** Cor.h
