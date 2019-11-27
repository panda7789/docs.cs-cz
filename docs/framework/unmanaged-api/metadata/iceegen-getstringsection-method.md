---
title: ICeeGen::GetStringSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: ba8da686d1834c81111828e9856525b96f575b93
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443262"
---
# <a name="iceegengetstringsection-method"></a>ICeeGen::GetStringSection – metoda
Načte řetězcovou reprezentaci oddílu kódu, na který odkazuje zadaný popisovač.  
  
 Tato metoda je zastaralá a neměla by se používat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `section`  
 [in, out] Popisovač části kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
