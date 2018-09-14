---
title: Funkce ConnectServerWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ConnectServerWmi používá model DCOM k vytvoření připojení k oboru názvů WMI.
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
ms.openlocfilehash: 163e61eef8a753b5b6470285e5e3ce63789e25a4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587646"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi – funkce
Připojení přes DCOM k oboru názvů WMI vytvoří v zadaném počítači.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
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

`strNetworkResource` [in] Ukazatel na platný `BSTR` , který obsahuje cestu k objektu správný obor názvů rozhraní WMI. Zobrazit [poznámky](#remarks) části Další informace.

`strUser` [in] Ukazatel na platný `BSTR` , která obsahuje uživatelské jméno. A `null` hodnota označuje aktuální kontext zabezpečení. Pokud se uživatel nachází v jiné doméně než tu, `strUser` může také obsahovat doména a uživatelské jméno oddělené zpětným lomítkem. `strUser` Můžete také být v uživatelském hlavní název (UPN) naformátovat, suhc jako *userName@domainName*. Zobrazit [poznámky](#remarks) části Další informace.

`strPassword` [in] Ukazatel na platný `BSTR` obsahující heslo. A `null` označuje aktuální kontext zabezpečení. Prázdný řetězec ("") označuje platné heslo nulové délky.

`strLocale` [in] Ukazatel na platný `BSTR` určující správné národní prostředí pro načítání informací. Identifikátory národního prostředí Microsoft formát řetězce je "MS\_*xxx*", kde *xxx* je řetězce v šestnáctkovém formátu, který určuje identifikátor národního prostředí (LCID). Pokud je zadán neplatný národní prostředí, vrátí metoda `WBEM_E_INVALID_PARAMETER` s výjimkou Windows 7, které místo toho používají výchozí národní prostředí serveru. Pokud se používá null1 aktuálního národního prostředí. 
 
`lSecurityFlags` [in] Příznaky, které mají být předány `ConnectServerWmi` metody. Hodnotu nula (0) pro tento parametr je výsledkem volání `ConnectServerWmi` vrací pouze po navázání připojení k serveru. To může způsobit aplikace neodpovídá po neomezenou dobu Pokud na serveru se přeruší. Platné hodnoty jsou:

| Konstanta  | Hodnota  | Popis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Vyhrazeno pro interní použití. Nepoužívejte. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` vrátí do dvou minut nebo i rychleji. |

`strAuthority` [in] Název domény uživatele. Může mít následující hodnoty:

| Hodnota | Popis |
|---------|---------|
| Prázdné | Bude použito ověřování NTLM a používá NTLM domény aktuálního uživatele. Pokud `strUser` Určuje doménu (doporučené umístění), nesmí být zadané tady. Funkce vrátí `WBEM_E_INVALID_PARAMETER` při zadání domény v obou parametrech. |
| Pomocí protokolu Kerberos:*hlavní název* | Používáno ověřování protokolem Kerberos a tento parametr obsahuje hlavní název Kerberos. |
| NTLMDOMAIN:*název domény* | Ověřování NT LAN Manager se používá, a tento parametr obsahuje název domény NTLM. |

`pCtx`   
[in] Obvykle je tento parametr je `null`. V opačném případě je ukazatel [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) podle jednoho nebo více dynamických tříd zprostředkovatelů je požadován objekt. 

`ppNamespace`  
[out] Po návratu funkce přijímá ukazatel [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objekt vázán na určený obor názvů. Je nastaven tak, aby odkazoval na `null` když dojde k chybě.

`impLevel`  
[in] Úroveň zosobnění.

`authLevel`  
[in] Úroveň autorizace.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v *WbemCli.h* hlavičkový soubor, nebo je definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Obecné selhání došlo. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nedostatek paměti je k dispozici k dokončení operace. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metody.

 Pro místní přístup k výchozí obor názvů `strNetworkResource` může být jednoduchý objekt cesta: "root\default" nebo "\\.\root\default". Pro přístup k výchozí obor názvů ve vzdáleném počítači pomocí modelu COM nebo Microsoft kompatibilní sítě, zahrnují název počítače: "\\myserver\root\default". Název počítače může také být, název DNS nebo IP adresu. `ConnectServerWmi` Funkce se také připojit pomocí počítače se systémem IPv6 pomocí adresy IPv6.

`strUser` Nemůže být prázdný řetězec. Pokud je v zadané doméně `strAuthority`, se nesmí být i součástí `strUser`, nebo funkce vrátí `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
