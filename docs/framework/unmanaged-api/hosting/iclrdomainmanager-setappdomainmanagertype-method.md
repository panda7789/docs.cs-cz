---
title: ICLRDomainManager::SetAppDomainManagerType – metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 89b3f9f248a445cc0568236d6a1df14269de4187
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615693"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType – metoda
Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAppDomainManagerAssembly`  
 pro Zobrazovaný název sestavení obsahujícího typ Správce aplikační domény; například: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 pro Název typu správce aplikační domény, včetně oboru názvů.  
  
 `dwInitializeDomainFlags`  
 pro Kombinace hodnot výčtu [EInitializeNewDomainFlags –](einitializenewdomainflags-enumeration.md) , které poskytují informace o Správci aplikačních domén.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
  
## <a name="remarks"></a>Poznámky  
 V současné době je jediná definovaná hodnota pro `dwInitializeDomainFlags` je `eInitializeNewDomainFlags_NoSecurityChanges` , což znamená, že modul CLR (Common Language Runtime), který správce aplikační domény nemění nastavení zabezpečení při provádění <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody. To umožňuje, aby CLR optimalizuje načítání sestavení, která mají podmíněný <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA). To může mít za následek výrazné zlepšení doby spuštění, pokud je přenosná uzávěra této sady sestavení velká.  
  
> [!IMPORTANT]
> Pokud hostitel určí `eInitializeNewDomainFlags_NoSecurityChanges` pro správce aplikační domény, <xref:System.InvalidOperationException> je vyvolána, pokud je proveden libovolný pokus o změnu zabezpečení domény aplikace.  
  
 Volání metody [ICLRControl:: SetAppDomainManagerType –](iclrcontrol-setappdomainmanagertype-method.md)je ekvivalentní volání `ICLRDomainManager::SetAppDomainManagerType` s `eInitializeNewDomainFlags_None` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Hostování](index.md)
- [ICLRDomainManager – rozhraní](iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags – výčet](einitializenewdomainflags-enumeration.md)
