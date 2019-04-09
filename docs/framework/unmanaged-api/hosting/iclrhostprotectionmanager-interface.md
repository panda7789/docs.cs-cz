---
title: ICLRHostProtectionManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd096344c987d8901f0baab86e370abbb03528e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177772"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager – rozhraní
Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole spouštění v částečně důvěryhodným kódem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Poskytuje záruku, že se nikdy vznikají některých výjimečných časování, které mohou způsobit závažná common language runtime (CLR) chyby.|  
|[SetProtectedCategories – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|Určuje kategorie spravované typy a členy, které by měl být blokovaný spouštění v částečně důvěryhodným kódem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EApiCategories – výčet](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
