---
title: PutInstanceWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce PutInstanceWmi vytvoří nebo aktualizuje instanci existující třídy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b33f31d69c64ce520580c29f1014c058c78d0953
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127354"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi – funkce

Vytvoří nebo aktualizuje instanci existující třídy. Instance je zapsána do úložiště rozhraní WMI.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>Parametry

`pInst`\
pro Ukazatel na instanci, která má být zapsána.

`lFlags`\
pro Kombinace příznaků, které mají vliv na chování této funkce. Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud je nastaveno, WMI neukládá žádné kvalifikátory se **změněným** charakterem. <br> Pokud není nastavena, předpokládá se, že tento objekt není lokalizován a že jsou všechny kvalifikátory uloženy s touto instancí. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0,8 | Vytvořte instanci, pokud neexistuje, nebo ji přepište, pokud už existuje. |
| `WBEM_FLAG_UPDATE_ONLY` | první | Aktualizujte instanci. Aby bylo volání úspěšné, musí instance existovat. |
| `WBEM_FLAG_CREATE_ONLY` | odst | Vytvořte instanci. Volání se nezdařilo, pokud instance již existuje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí volání semisynchronní. |

`pCtx`\
pro Tato hodnota je obvykle `null`. V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.

`ppCallResult`\
mimo Pokud `null`, tento parametr se nepoužívá. Pokud `lFlags` obsahuje `WBEM_FLAG_RETURN_IMMEDIATELY`, funkce se vrátí hned `WBEM_S_NO_ERROR`. Parametr `ppCallResult` přijme ukazatel na nový objekt [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k aktualizaci instance zadané třídy. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Třída podporující tuto instanci není platná. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | byla zadána `null` pro vlastnost, která nemůže být `null`, například ta, která je označena **indexovaným** nebo **Not_Null** kvalifikátorem. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Zadaná instance není platná. (Například volání `PutInstanceWmi` s třídou vrátí tuto hodnotu.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | Byl zadán příznak `WBEM_FLAG_CREATE_ONLY`, ale instance již existuje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | v `lFlags`byla zadána `WBEM_FLAG_UPDATE_ONLY`, ale instance neexistuje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartována. Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [Služby IWbem::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .

Funkce `PutInstanceWmi` podporuje vytváření instancí a aktualizaci instancí stávajících tříd.  V závislosti na tom, jak je nastaven parametr `pCtx`, jsou aktualizovány buď některé nebo všechny vlastnosti instance.

Když instance, na kterou ukazuje `pInst`, patří do podtřídy, Správa systému Windows volá všechny poskytovatele zodpovědné za třídy, ze kterých je odvozená podtřída. Všechny tyto zprostředkovatele musí být úspěšné, aby původní `PutInstanceWmi` požadavek uspěl. Zprostředkovatel podporující nejvyšší třídu v hierarchii je označován jako první. Pořadí volání pokračuje s podtřídou nejvyšší třídy a pokračuje shora dolů, dokud Správa systému Windows nedosáhne poskytovatele pro třídu vlastnící instanci, na kterou ukazuje `pInst`.
Správa systému Windows nevolá poskytovatele pro žádnou z podřízených tříd instance.

Když aplikace musí aktualizovat instanci, která patří do hierarchie tříd, parametr `pInst` musí ukazovat na instanci obsahující vlastnosti, které mají být upraveny. To znamená, že zvažte cílovou instanci, která patří do **ClassB**. Instance **ClassB** je odvozena z **třídy Class**a **Třída Class** definuje vlastnost **propa**. Pokud aplikace chce provést změnu hodnoty **propa** v instanci **ClassB** , musí nastavit `pInst` na tuto instanci, nikoli na instanci **třídy Class**.

Volání `PutInstanceWmi` na instanci abstraktní třídy není povoleno.

Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
