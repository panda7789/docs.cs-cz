---
title: Funkce ExecQueryWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ExecQueryWmi spustí dotaz pro načtení objektů.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 402bbcb9ad5e462a55c5ec2716417f512f03ee19
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373215"
---
# <a name="execquerywmi-function"></a>Funkce ExecQueryWmi

Spustí dotaz pro načtení objektů.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ExecQueryWmi (
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
[in] Kombinace příznaků, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

| Konstanta | Hodnota  | Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sada funkce načte upravenou kvalifikátory uložené v lokalizovaných názvů národního prostředí aktuálního připojení. <br/> Pokud není sada, funkce načte jenom v kvalifikátorech uložené v oboru názvů okamžité. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že volání semisynchronní volání. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor pouze vpřed. Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Rozhraní WMI uchovává ukazatelů na objekty ve výčtu, dokud se neuvolní. |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zajišťuje, že některé vrátí objekty mají dostatek informací v nich tak této vlastnosti systému jako **__PATH**, **__RELPATH**, a **__SERVER**, nejsou `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Tento příznak se používá pro vytváření prototypů. Nelze spustit dotaz a místo toho vrátí objekt, který vypadá jako obvykle za následek objektu. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Způsobí, že přímý přístup k poskytovateli pro zadaný bez ohledu na jeho nadřazené třídu nebo jakékoli podtřídy třídy. |

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro zajištění nejlepšího výkonu.

`pCtx`\
[in] Obvykle je tato hodnota `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.

`ppEnum`\
[out] Pokud nenastane žádná chyba přijímá ukazatel na enumerátor, který umožňuje volajícímu načtení instancí v sadě výsledků dotazu. Dotaz může mít nula instancemi sady výsledků. Zobrazit [poznámky](#remarks) části Další informace.

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

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jeden nebo více tříd, které funkce může vrátit. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k nespecifikované chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Dotazu došlo k chybě syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Požadovaný jazyk dotazu není podporován. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Dotaz je příliš složitý. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Dotaz Určuje třídu, která neexistuje. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) metody.

Tato funkce zpracuje dotaz zadaný v `strQuery` parametr a vytvoří čítač přes který může volající přístup výsledky dotazu. Enumerátor je ukazatel [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) rozhraní; dotaz výsledky jsou instance třídy objektů k dispozici prostřednictvím [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) rozhraní.

Existují omezení počtu `AND` a `OR` klíčová slova, které lze použít v dotazech WQL. Velký počet klíčových slov jazyka WQL použit ve složitých dotazů může způsobit rozhraní WMI se vraťte `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) kód chyby jako `HRESULT` hodnotu. Limit klíčová slova jazyka WQL závisí na tom, jak složitá je dotaz.

Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)