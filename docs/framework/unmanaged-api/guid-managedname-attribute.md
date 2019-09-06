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
ms.openlocfilehash: 110d6eb0abcf4b4ce73f1ee9d27e27122f360270
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374440"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName – atribut
Definuje vlastní atribut rozhraní, který určuje název spravovaného oboru názvů pro knihovnu modelu COM (Component Object Model).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 Název spravovaného oboru názvů pro knihovnu.  
  
## <a name="definition"></a>Definice  
 `GUID_ManagedName`je definována v cor. h následujícím způsobem:  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Poznámky  
 Vlastní atribut rozhraní definuje metadata pro objekt v knihovně typů.  
  
 Použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> nebo<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> k načtení spravovaného názvu z atributu.  
  
 Další informace naleznete v tématu [atributy rozhraní](/cpp/windows/attributes/interface-attributes) v dokumentaci Visual C++ reference.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici knihovny pomocí `GUID_ManagedName` atributu.  
  
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
 **Hlaviček** Cor. h
