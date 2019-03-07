---
title: ICLRRuntimeInfo::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbfa25300cbed83d36cc43d9a0dd0beb2520dea1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475287"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString – metoda
Získá common language runtime (CLR) informace o verzi přidružené danou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.  
  
 Tato metoda nahrazuje následující funkce:  
  
-   [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 [out] Kompilace rozhraní .NET Framework verze ve formátu "v*A*. *B*[. *X*] ". *A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení. *X* je volitelný. Pokud *X* není k dispozici není žádné koncové tečky.  
  
> [!NOTE]
>  Tento parametr musí odpovídat názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework.  
  
 Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *x*", kde *x* závisí na číslo sestavení nainstalována. Všimněte si, že předpona "v" je povinný.  
  
 `pchBuffer`  
 [out v] Určuje velikost `pwzBuffer` , aby přetečení vyrovnávací paměti. Pokud `pwzBuffer` je `null`, `pchBuffer` vrátí velikost požadované `pwzBuffer` povolit předběžné přidělování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzBuffer` nebo `pchBuffer` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
