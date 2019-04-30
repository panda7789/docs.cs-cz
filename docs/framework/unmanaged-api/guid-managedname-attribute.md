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
ms.openlocfilehash: 48ad6e4d1d03d8362123e65f16907880b18893f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777907"
---
# <a name="guidmanagedname-attribute"></a>GUID_ManagedName – atribut
Definuje atribut vlastní rozhraní, který určuje název spravovaného oboru názvů pro knihovny součásti object model (COM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Název oboru názvů spravované knihovny.  
  
## <a name="definition"></a>Definice  
 `GUID_ManagedName` je definován v Cor.h následujícím způsobem:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Poznámky  
 Atribut typu vlastního rozhraní definuje metadata pro objekt v knihovně typů.  
  
 Použití <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> načíst spravované název z atributu.  
  
 Další informace najdete v tématu [atributy rozhraní](/cpp/windows/interface-attributes) v jazyce Visual C++ referenční dokumentaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití definice knihovny `GUID_ManagedName` atribut.  
  
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
