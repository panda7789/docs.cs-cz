---
title: COINITIEE – výčet
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005905"
---
# <a name="coinitiee-enumeration"></a>COINITIEE – výčet
Určuje konstanty, které používá [CoInitializeEE –](../hosting/coinitializeee-function.md) při inicializaci modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Výchozí režim inicializace. Tím se Inicializuje modul runtime a vytvoří se výchozí hodnota <xref:System.AppDomain> .|  
|`COINITEE_DLL`|Inicializuje spuštění spravované knihovny DLL.|  
|`COINITEE_MAIN`|Inicializuje pro spuštění spravovaného souboru EXE. Tím se Inicializuje modul runtime, ale nevytvoří se výchozí <xref:System.AppDomain> , který se vytvoří po vstupu do hlavní rutiny exe.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
