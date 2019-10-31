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
ms.openlocfilehash: 3859752fd92a76f3fef1ceced0e792109b65106a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108282"
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
|`guidScheme`|Entita, která přidá odkaz V tomto poli může být jedna z následujících hodnot:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: na sestavení odkazuje aplikace, která byla nainstalována pomocí Instalační služba systému Windows Microsoft. Pole `szIdentifier` je nastavené na `MSI`a pole `szNonCanonicalData` je nastavené na `Windows Installer`. Toto schéma se používá pro souběžná sestavení Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: na sestavení odkazuje aplikace, která se zobrazí v rozhraní **Přidat nebo odebrat programy** . Pole `szIdentifier` poskytuje token, který registruje aplikaci pomocí rozhraní **Přidat nebo odebrat programy** .<br />-FUSION_REFCOUNT_FILEPATH_GUID: na sestavení odkazuje aplikace, která je reprezentovaná souborem v systému souborů. Pole `szIdentifier` poskytuje cestu k tomuto souboru.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: na sestavení odkazuje aplikace, která je zastoupena pouze neprůhledným řetězcem. Pole `szIdentifier` poskytuje tento neprůhledný řetězec. Globální mezipaměť sestavení (GAC) neprovádí kontrolu existence neprůhledných odkazů při odebrání této hodnoty.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Tato hodnota je vyhrazená.|  
|`szIdentifier`|Jedinečný řetězec, který identifikuje aplikaci, která nainstalovala sestavení do globální mezipaměti sestavení (GAC). Jeho hodnota je závislá na hodnotě pole `guidScheme`.|  
|`szNonCanonicalData`|Řetězec, který rozumí pouze entita, která přidá odkaz. Globální mezipaměť sestavení (GAC) ukládá tento řetězec, ale nepoužívá ho.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro fúze](fusion-structures.md)
- [Globální mezipaměť sestavení](../../app-domains/gac.md)
