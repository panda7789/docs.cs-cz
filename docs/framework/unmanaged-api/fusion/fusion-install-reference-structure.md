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
ms.openlocfilehash: 4685d1a23fdf1874817522a16ccd428d81acd1ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE – struktura
Představuje odkaz, který umožňuje aplikaci na sestavení, který má aplikace nainstalované v globální mezipaměti sestavení.  
  
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
|`guidScheme`|Typ entity, která přidá odkaz. Toto pole může mít jednu z následujících hodnot:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: Odkazuje sestavení aplikace, která byla nainstalována pomocí Instalační služby systému Windows. `szIdentifier` Je nastaveno na `MSI`a `szNonCanonicalData` je nastaveno na `Windows Installer`. Toto schéma se používá pro Windows souběžně sdílená sestavení.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Sestavení odkazuje aplikace, která se zobrazí v **přidat nebo odebrat programy** rozhraní. `szIdentifier` Pole poskytuje token, který aplikace se zaregistruje **přidat nebo odebrat programy** rozhraní.<br />-FUSION_REFCOUNT_FILEPATH_GUID: Odkazuje sestavení aplikace, která je reprezentována souboru v systému souborů. `szIdentifier` Pole obsahuje cestu k souboru.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: Odkazuje sestavení aplikace, která je reprezentována pouze neprůhledný řetězec. `szIdentifier` Pole poskytuje toto neprůhledný řetězec. Když odeberete tuto hodnotu nekontroluje existenci neprůhledného odkazy globální mezipaměti sestavení.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je rezervovaná.|  
|`szIdentifier`|Jedinečného řetězce, který identifikuje aplikaci, která nainstalována sestavení v globální mezipaměti sestavení. Jeho hodnota závisí na hodnotu `guidScheme` pole.|  
|`szNonCanonicalData`|Řetězec, který se rozumí pouze typ entity, která přidá odkaz. Globální mezipaměti sestavení ukládá tento řetězec, ale nepoužívá se.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)
