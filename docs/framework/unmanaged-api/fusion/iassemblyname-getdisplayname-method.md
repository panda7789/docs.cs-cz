---
title: IAssemblyName::GetDisplayName – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134370"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName – metoda
Získá název sestavení, na které odkazuje tento objekt [IAssemblyName](iassemblyname-interface.md) , do čitelného lidského.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDisplayName`  
 mimo Vyrovnávací paměť řetězců, která obsahuje název odkazovaného sestavení.  
  
 `pccDisplayName`  
 [in, out] Velikost `szDisplayName` v různých znacích, včetně ukončovacího znaku null.  
  
 `dwDisplayFlags`  
 pro Bitová kombinace hodnot [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) , které ovlivňují funkce `szDisplayName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [Výčty pro fúze](fusion-enumerations.md)
