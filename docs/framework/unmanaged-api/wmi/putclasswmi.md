---
title: PutClassWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce PutClassWmi vytvoří novou třídu nebo aktualizuje stávající.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101781"
---
# <a name="putclasswmi-function"></a>PutClassWmi – funkce

Vytvoří novou třídu nebo aktualizuje stávající.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametry

`pObject`\
pro Ukazatel na platnou definici třídy. Musí být správně inicializován se všemi požadovanými hodnotami vlastností.

`lFlags`\
pro Kombinace příznaků, které mají vliv na chování této funkce. Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud je nastaveno, WMI neukládá žádné kvalifikátory se změněným charakterem. <br> Pokud není nastavena, předpokládá se, že tento objekt není lokalizován a že jsou všechny kvalifikátory uloženy s touto instancí. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0,8 | Vytvořte třídu, pokud neexistuje, nebo ji přepište, pokud již existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | první | Aktualizujte třídu. Aby bylo volání úspěšné, musí třída existovat. |
| `WBEM_FLAG_CREATE_ONLY` | odst | Vytvořte třídu. Volání se nezdařilo, pokud již třída existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí volání semisynchronní. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Poskytovatelé nabízených oznámení musí zadat tento příznak při volání `PutClassWmi` k označení toho, že se tato třída změnila. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0,8 | Umožňuje aktualizovat třídu, pokud nejsou žádné odvozené třídy a žádné instance této třídy. Také umožňuje aktualizace ve všech případech, pokud je změna pouze neimportované kvalifikátory, jako je například kvalifikátor Description. Pokud má třída instance nebo změny důležité kvalifikátory, aktualizace se nezdařila. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Umožňuje aktualizace tříd i v případě, že existují podřízené třídy, pokud změna nezpůsobí konflikty s podřízenými třídami. Tento příznak například umožňuje přidat novou vlastnost do základní třídy, která nebyla dříve uvedena v žádné z podřízených tříd. Pokud má třída instance, aktualizace se nezdařila. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | vynutí aktualizace tříd, pokud existují konfliktní podřízené třídy. Například tento příznak vynutí aktualizaci, pokud je kvalifikátor třídy definován v podřízené třídě a základní třída se pokusí přidat stejný kvalifikátor, který je v konfliktu s existujícím. V režimu vynucení tis konflikt je vyřešen odstraněním kolidujícího kvalifikátoru v podřízené třídě. |

`pCtx`\
pro Tato hodnota je obvykle `null`. V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.

`ppCallResult`\
mimo Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce se vrátí hned `WBEM_S_NO_ERROR`. Parametr `ppCallResult` přijme ukazatel na nový objekt [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k vytváření nebo změnám tříd. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Zadaná třída není platná. Obvykle to znamená, že `pObject` určuje objekt instance. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Zadaný název třídy není platný. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Byl proveden pokus o provedení změny, která by způsobila neplatnost podtřídy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | Byl zadán příznak `WBEM_FLAG_CREATE_ONLY`, ale třída již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` byl zadán v `lFlags`a Třída nebyla nalezena. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Nebyly nastaveny všechny požadované vlastnosti pro třídy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartována. Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [Služby IWbem::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .

Uživatel nemůže vytvořit třídy s názvy, které začínají nebo končí znakem podtržítka.

Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
