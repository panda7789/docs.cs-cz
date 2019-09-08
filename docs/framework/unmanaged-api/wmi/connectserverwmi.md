---
title: ConnectServerWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce ConnectServerWmi používá model DCOM k vytvoření připojení k oboru názvů rozhraní WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ebb268dcee877f4e9aea0c88852333897030dd1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798749"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi – funkce

Vytvoří připojení prostřednictvím modelu DCOM k oboru názvů WMI v zadaném počítači.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a>Parametry

`strNetworkResource`\
pro Ukazatel na platný `BSTR` , který obsahuje cestu k objektu správného oboru názvů rozhraní WMI. Další informace najdete v části [poznámky](#remarks) .

`strUser`\
pro Ukazatel na platný `BSTR` , který obsahuje uživatelské jméno. `null` Hodnota označuje aktuální kontext zabezpečení. Pokud uživatel pochází z jiné domény než z aktuální, `strUser` může také obsahovat doménu a uživatelské jméno oddělené zpětným lomítkem. `strUser`může být také ve formátu hlavního názvu uživatele (UPN), například `userName@domainName`. Další informace najdete v části [poznámky](#remarks) .

`strPassword`\
pro Ukazatel na platný `BSTR` , který obsahuje heslo. A `null` označuje aktuální kontext zabezpečení. Prázdný řetězec ("") označuje platné heslo s nulovou délkou.

`strLocale`\
pro Ukazatel na platný `BSTR` , který označuje správné národní prostředí pro načtení informací. V případě identifikátorů národního prostředí společnosti Microsoft je formát řetězce "MS\_*xxx*", kde *xxx* je řetězec v šestnáctkovém formátu, který označuje identifikátor národního prostředí (LCID). Pokud je zadáno neplatné národní prostředí, vrátí `WBEM_E_INVALID_PARAMETER` se metoda s výjimkou systému Windows 7, kde je místo toho použito výchozí národní prostředí serveru. Pokud je použito ' NULL1 ', aktuální národní prostředí.

`lSecurityFlags`\
pro Příznaky, které mají být `ConnectServerWmi` předána metodě. Hodnota nula (0) pro tento parametr způsobí, že volání `ConnectServerWmi` bude vráceno pouze po navázání připojení k serveru. To může způsobit, že aplikace nereaguje na neomezenou dobu, pokud je server poškozený. Další platné hodnoty jsou:

| Konstanta  | Value  | Popis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Vyhrazeno pro interní použití. Nepoužívejte. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi`Vrátí dvě minuty nebo méně. |

`strAuthority`\
pro Název domény uživatele Může mít následující hodnoty:

| Value | Popis |
|---------|---------|
| trhnout | Používá se ověřování NTLM a doména NTLM aktuálního uživatele se používá. Pokud `strUser` určuje doménu (doporučené umístění), nesmí se tady zadat. Funkce se vrátí `WBEM_E_INVALID_PARAMETER` , pokud zadáte doménu v obou parametrech. |
| Kerberos:*hlavní název* | Použije se ověřování protokolem Kerberos a tento parametr obsahuje hlavní název protokolu Kerberos. |
| NTLMDOMAIN:*název domény* | Použije se ověřování NT LAN Manageru a tento parametr obsahuje název domény NTLM. |

`pCtx`\
pro Obvykle je `null`tento parametr. V opačném případě se jedná o ukazatel na objekt [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , který vyžaduje jeden nebo více zprostředkovatelů dynamické třídy.

`ppNamespace`\
mimo Když se funkce vrátí, přijme ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) vázaný na zadaný obor názvů. Je nastavená tak, aby `null` odkazovala na chybu.

`impLevel`\
pro Úroveň zosobnění.

`authLevel`\
pro Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .

Pro místní přístup k výchozímu oboru názvů `strNetworkResource` může být cesta jednoduchého objektu: "root\default" nebo "\\.\root\default". Pro přístup k výchozímu oboru názvů na vzdáleném počítači pomocí modelu COM nebo sítě kompatibilního se společností Microsoft zadejte název počítače\\: "myserver\root\default". Název počítače může být taky název DNS nebo IP adresa. `ConnectServerWmi` Funkce se také může připojit k počítačům s protokolem IPv6 pomocí adresy IPv6.

`strUser`nemůže být prázdný řetězec. Pokud je doména určena v `strAuthority`, nesmí být také obsažena v `strUser`nebo funkce vrácena `WBEM_E_INVALID_PARAMETER`.

## <a name="requirements"></a>Požadavky

 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

 **Hlaviček** WMINet_Utils.idl

 **Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
