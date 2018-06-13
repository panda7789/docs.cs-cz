---
title: Funkce ConnectServerWmi (referenční dokumentace nespravovaného rozhraní API)
description: Funkce ConnectServerWmi DCOM používá k vytvoření připojení k oboru názvů WMI.
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
ms.openlocfilehash: de8447b9b090fc7f53df23346d61932bcb4dd6ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461994"
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi – funkce
Vytvoří připojení přes DCOM k oboru názvů WMI v zadaném počítači.  
  
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

`strNetworkResource` [v] Ukazatel na platnou `BSTR` obsahující cestu objektu správný obor názvů rozhraní WMI. Najdete v článku [poznámky](#remarks) části Další informace.

`strUser` [v] Ukazatel na platnou `BSTR` obsahující uživatelské jméno. A `null` hodnota označuje aktuální kontext zabezpečení. Pokud je uživatel z jiné domény než aktuální, `strUser` může také obsahovat doména a uživatelské jméno, které jsou oddělené zpětným lomítkem. `strUser` Můžete také být v uživatele hlavní název (UPN) formátovat, suhc jako *userName@domainName*. Najdete v článku [poznámky](#remarks) části Další informace.

`strPassword` [v] Ukazatel na platnou `BSTR` obsahující heslo. A `null` označuje aktuální kontext zabezpečení. Prázdný řetězec ("") označuje platné heslo nulové délky.

`strLocale` [v] Ukazatel na platnou `BSTR` určující správné národní prostředí pro načítání informací. Identifikátory národního prostředí Microsoft je formát řetězce "MS\_*xxx*", kde *xxx* je řetězce v šestnáctkovém formátu, který označuje identifikátor národního prostředí (LCID). Pokud je zadán neplatný národního prostředí, vrátí metoda `WBEM_E_INVALID_PARAMETER` s výjimkou ve Windows 7, kde bude místo něj použita výchozí národní prostředí serveru. Pokud se používá null1, aktuální národní prostředí. 
 
`lSecurityFlags` [v] Příznaky, které mají být předány `ConnectServerWmi` metoda. Hodnota nula (0) pro tento parametr je výsledkem volání `ConnectServerWmi` vrací pouze po vytvoření připojení k serveru. Výsledkem může být aplikace neodpovídá po neomezenou dobu Pokud server se přeruší. Platné hodnoty jsou:

| Konstanta  | Hodnota  | Popis  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0x40 | Vyhrazeno pro interní použití. Nepoužívejte. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` Vrátí za dvě minuty nebo méně. |

`strAuthority` [v] Název domény uživatele. Může mít následující hodnoty:

| Hodnota | Popis |
|---------|---------|
| Prázdné | Použít ověřování NTLM a NTLM domény aktuálního uživatele se používá. Pokud `strUser` Určuje doménu (doporučené umístění), nesmí být zadaný v tomto poli. Funkce vrátí hodnotu `WBEM_E_INVALID_PARAMETER` Pokud v oba parametry zadejte doménu. |
| Pomocí protokolu Kerberos:*hlavní název* | Používáno ověřování protokolem Kerberos a tento parametr obsahuje hlavní název protokolu Kerberos. |
| NTLMDOMAIN:*název domény* | Se používá ověřování NT LAN Manager a tento parametr obsahuje název domény protokolu NTLM. |

`pCtx`   
[v] Obvykle je tento parametr je `null`. Jinak je ukazatel na [IWbemContext](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) vyžaduje jeden nebo více poskytovatelů dynamické třídy objektu. 

`ppNamespace`  
[out] V případě, že funkce vrátí hodnotu, obdrží ukazatel na [Služby IWbem](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) vázaný objekt pro zadaný obor názvů. Je nastaven tak, aby odkazoval `null` když dojde k chybě.

`impLevel`  
[v] Úroveň zosobnění.

`authLevel`  
[v] Úroveň ověřování.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty, vrátí tato funkce jsou definovány v *WbemCli.h* soubor hlaviček, případně je možné definovat je jako konstanty ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Došlo k obecné chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Je k dispozici k dokončení operace není dostatek paměti. |
| `WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zabalí volání [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) metoda.

 Pro místní přístup k výchozí obor názvů `strNetworkResource` může být cesta jednoduchého objektu: "root\default" nebo "\\.\root\default". Pro přístup k výchozí obor názvů na vzdáleném počítači pomocí modelu COM nebo kompatibilní se službou Microsoft sítě, zahrnují název počítače: "\\myserver\root\default". Název počítače může také být, název DNS nebo IP adresu. `ConnectServerWmi` Funkce se může připojit i s počítači se systémem IPv6 pomocí adresy IPv6.

`strUser` nemůže být prázdný řetězec. Jestliže se v doméně `strAuthority`, se nesmí být zahrnuto do `strUser`, nebo funkce vrátí hodnotu `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také  
[Rozhraní WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
