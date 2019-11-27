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
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444113"
---
# <a name="coinitiee-enumeration"></a>COINITIEE – výčet
Určuje konstanty, které používá [CoInitializeEE –](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) při inicializaci modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Výchozí režim inicializace. Tím se Inicializuje modul runtime a vytvoří se výchozí <xref:System.AppDomain>.|  
|`COINITEE_DLL`|Inicializuje spuštění spravované knihovny DLL.|  
|`COINITEE_MAIN`|Inicializuje pro spuštění spravovaného souboru EXE. Tím se Inicializuje modul runtime, ale nevytvoří se výchozí <xref:System.AppDomain>, který se vytvoří po zadání hlavní rutiny EXE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
