---
title: FUSION_INSTALL_REFERENCE – struktura
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110362"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE – struktura
Představuje odkaz, který aplikace slouží k sestavení aplikace nainstalované v globální mezipaměti sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`cbSize`|Velikost struktury v bajtech.|  
|`dwFlags`|Vyhrazeno pro budoucí rozšíření. Tato hodnota musí být 0 (nula).|  
|`guidScheme`|Entita, která přidá odkaz. Toto pole může mít jednu z následujících hodnot:<br /><br /> -   FUSION_REFCOUNT_MSI_GUID: Sestavení se odkazuje aplikaci, která byla nainstalována pomocí Instalační služby systému Windows. `szIdentifier` Je nastaveno na `MSI`a `szNonCanonicalData` je nastaveno na `Windows Installer`. Toto schéma se používá pro sestavení vedle sebe Windows.<br />-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Sestavení se odkazuje, který se zobrazí v aplikaci **přidat nebo odebrat programy** rozhraní. `szIdentifier` Pole obsahuje token, který zaregistruje aplikaci **přidat nebo odebrat programy** rozhraní.<br />-   FUSION_REFCOUNT_FILEPATH_GUID: Sestavení se odkazuje v aplikaci, která je reprezentována souboru v systému souborů. `szIdentifier` Pole obsahuje cestu k tomuto souboru.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Aplikace, která je reprezentována pouze neprůhledný řetězec odkazuje sestavení. `szIdentifier` Pole obsahuje tento neprůhledný řetězec. Když odeberete tato hodnota nekontroluje existenci neprůhledné odkazy na globální mezipaměti sestavení.<br />-   FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je rezervovaná.|  
|`szIdentifier`|Jedinečný řetězec, který identifikuje aplikaci, která nainstalovaná sestavení v globální mezipaměti sestavení. Jeho hodnota závisí na hodnotě `guidScheme` pole.|  
|`szNonCanonicalData`|Řetězec, který je srozumitelné pouze entity, která přidá odkaz. Globální mezipaměti sestavení ukládá tento řetězec, ale nepoužívá se.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)
