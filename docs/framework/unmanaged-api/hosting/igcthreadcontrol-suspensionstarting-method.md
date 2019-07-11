---
title: IGCThreadControl::SuspensionStarting – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cb58593a30b855c9fabf55a6ca0a50886dc371f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779486"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a>IGCThreadControl::SuspensionStarting – metoda
Upozorňuje hostitele, že modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a>Poznámky  
 Nelze změnit plán žádného vlákna během `SuspensionStarting` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IGCThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
