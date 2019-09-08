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
ms.openlocfilehash: 9e81fb7c99b9fd03a69456a84f2191770f40121d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795345"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE – struktura
Představuje odkaz, který aplikace provede na sestavení, které aplikace nainstalovala v globální mezipaměti sestavení (GAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`guidScheme`|Entita, která přidá odkaz V tomto poli může být jedna z následujících hodnot:<br /><br /> -   FUSION_REFCOUNT_MSI_GUID: Na sestavení odkazuje aplikace, která byla nainstalována pomocí Instalační služba systému Windows Microsoft. Pole je nastaveno na `MSI`hodnotu a `szNonCanonicalData` pole je nastaveno na `Windows Installer`. `szIdentifier` Toto schéma se používá pro souběžná sestavení Windows.<br />- FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Na sestavení odkazuje aplikace, která se zobrazí v rozhraní **Přidat nebo odebrat programy** . Pole poskytuje token, který registruje aplikaci pomocí rozhraní **Přidat nebo odebrat programy.** `szIdentifier`<br />-   FUSION_REFCOUNT_FILEPATH_GUID: Na sestavení se odkazuje aplikace, která je reprezentovaná souborem v systému souborů. `szIdentifier` Pole poskytuje cestu k tomuto souboru.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: Na sestavení odkazuje aplikace, která je zastoupena pouze neprůhledným řetězcem. `szIdentifier` Pole poskytuje tento neprůhledný řetězec. Globální mezipaměť sestavení (GAC) neprovádí kontrolu existence neprůhledných odkazů při odebrání této hodnoty.<br />- FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je vyhrazena.|  
|`szIdentifier`|Jedinečný řetězec, který identifikuje aplikaci, která nainstalovala sestavení do globální mezipaměti sestavení (GAC). Jeho hodnota závisí na hodnotě `guidScheme` pole.|  
|`szNonCanonicalData`|Řetězec, který rozumí pouze entita, která přidá odkaz. Globální mezipaměť sestavení (GAC) ukládá tento řetězec, ale nepoužívá ho.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](fusion-structures.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
