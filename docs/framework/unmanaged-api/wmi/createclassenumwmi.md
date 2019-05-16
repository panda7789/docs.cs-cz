---
title: Funkce CreateClassEnumWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce CreateClassEnumWmi vrátí enumerátor pro všechny třídy, které splňují zadaná kritéria.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3777319f818b7652157147f458b81d9935805b1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636992"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi – funkce
Vrátí enumerátor pro všechny třídy, které splňují kritéria zadaná výběru.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

`strSuperclass`\
[in] Pokud není `null` nebo prázdnou, určí název nadřazené třídu; vrátí enumerátor pouze podtřídy této třídy. Pokud je `null` nebo prázdné a `lFlags` WBEM_FLAG_SHALLOW se vrátí jenom nejvyšší úrovně třídy (třídy s žádnou nadřazené třídu). Pokud je `null` nebo prázdné a `lFlags` je `WBEM_FLAG_DEEP`, vrátí všechny třídy v oboru názvů.

`lFlags`\
[in] Kombinace příznaků, které ovlivňují chování této funkce. Následující hodnoty jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud sada funkce načte upravenou kvalifikátory uložené v lokalizovaných názvů národního prostředí aktuálního připojení. <br/> Pokud není sada, funkce načte jenom v kvalifikátorech uložené v oboru názvů okamžité. |
| `WBEM_FLAG_DEEP` | 0 | Výčet zahrnuje všechny podtřídy v hierarchii, ale ne této třídy. |
| `WBEM_FLAG_SHALLOW` | 1 | Výčet obsahuje pouze čistě instance této třídy a vyloučí všechny výskyty podtříd zadat vlastnosti nebyla nalezena v této třídě. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí, že volání semisynchronní volání. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Vrátí enumerátor pouze vpřed. Obvykle dopředné enumerátory jsou rychlejší a využívat méně paměti, než je běžné výčty, ale nejsou povoleny volání [klonování](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Rozhraní WMI uchovává ukazatelů na objekty ve výčtu, dokud se neuvolní. |

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro zajištění nejlepšího výkonu.

`pCtx`\
[in] Obvykle je tato hodnota `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , jež lze použít poskytovatele, který poskytuje požadované třídy.

`ppEnum`\
[out] Přijímá ukazatel na enumerátor.

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
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` neexistuje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartování. Volání [ConnectServerWmi](connectserverwmi.md) znovu. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Odkaz vzdálené volání (procedur RPC) mezi aktuálním procesem a službou WMI se nezdařil. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) metody.

Pokud selže volání funkce, můžete získat další informace o chybě při volání [GetErrorInfo –](geterrorinfo.md) funkce.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** WMINet_Utils.idl

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
