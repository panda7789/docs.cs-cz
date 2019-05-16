---
title: Funkce ExecNotificationQueryWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ExecNotificationQueryWmi provede dotaz přijímat události.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa2233bab82f3cd4d1bbcb59f5714c6e4dc91aa5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636565"
---
# <a name="execnotificationquerywmi-function"></a>Funkce ExecNotificationQueryWmi

Provede dotaz přijímat události. Volání se vrátí okamžitě a volající může dotazovat vrácené enumerátor pro události při jejich doručení. Uvolnění vrácené enumerátor zruší dotazu.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a>Parametry

`strQueryLanguage`\
[in] Řetězec s platnou dotazovací jazyk Windows Management podporuje. Musí být "WQL", používá zkratka dotazovacího jazyka rozhraní WMI.

`strQuery`\
[in] Text dotazu. Tento parametr nemůže mít `null`.

`lFlags`\
[in] Kombinace následující dva příznaky, které ovlivňují chování této funkce. Tyto hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty ve vašem kódu.

| Konstanta | Value  | Popis  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že volání semisynchronní volání. Pokud není tento příznak nastaven, volání selže. Je to proto průběžně přijetí události to znamená, že uživatel se musí dotazovat vrácené enumerátor. Po neomezenou dobu blokování toto volání, který je nemožné. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor pouze vpřed. Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md). |

`pCtx`\
[in] Obvykle je tato hodnota `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované události.

`ppEnum`\
[out] Pokud nenastane žádná chyba přijímá ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu. Zobrazit [poznámky](#remarks) části Další informace.

`authLevel`\
[in] Úroveň autorizace.

`impLevel`\
[in] Úroveň zosobnění.

`pCurrentNamespace`\
[in] Ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt, který představuje aktuální obor názvů.

`strUser`\
[in] Uživatelské jméno. Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strPassword`\
[in] Heslo. Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

`strAuthority`\
[in] Název domény uživatele. Zobrazit [ConnectServerWmi](connectserverwmi.md) funkce pro další informace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které funkce může vrátit. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Dotaz Určuje třídu, která neexistuje. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Příliš mnoho přesnost při doručování událostí, které se požaduje. Je třeba zadat větší tolerance cyklického dotazování. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Dotaz požaduje více informací, než může poskytnout správy Windows. To `HRESULT` je vrácena, když dotaz události výsledkem požadavku dotazování všechny objekty v oboru názvů. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Dotazu došlo k chybě syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Požadovaný jazyk dotazu není podporován. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Dotaz je příliš složitý. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Dotaz nelze parsovat. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) metody.

Po vrácení funkce volající předá pravidelně vráceného `ppEnum` objektu [Další](next.md) funkcí, pokud jsou k dispozici žádné události.

Existují omezení počtu `AND` a `OR` klíčová slova, které lze použít v dotazech WQL. Velký počet klíčových slov jazyka WQL použit ve složitých dotazů může způsobit rozhraní WMI se vraťte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu. Limit klíčová slova jazyka WQL závisí na tom, jak složitá je dotaz.

Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
