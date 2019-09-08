---
title: CreateClassEnumWmi – funkce (Reference nespravovaného rozhraní API)
description: Funkce CreateClassEnumWmi vrací enumerátor pro všechny třídy, které odpovídají zadaným kritériím.
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
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798740"
---
# <a name="createclassenumwmi-function"></a>CreateClassEnumWmi – funkce
Vrátí enumerátor pro všechny třídy, které odpovídají zadaným kritériím výběru.

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
pro Pokud není `null` nebo prázdné, určuje název nadřazené třídy; enumerátor vrátí pouze podtřídy této třídy. Pokud je `null` nebo prázdný a `lFlags` je WBEM_FLAG_SHALLOW, vrátí pouze třídy nejvyšší úrovně (třídy bez nadřazené třídy). Pokud je `null` nebo prázdný a `lFlags` je `WBEM_FLAG_DEEP`, vrátí všechny třídy v oboru názvů.

`lFlags`\
pro Kombinace příznaků, které mají vliv na chování této funkce. Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení. <br/> Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů. |
| `WBEM_FLAG_DEEP` | 0 | Výčet zahrnuje všechny podtřídy v hierarchii, ale ne tuto třídu. |
| `WBEM_FLAG_SHALLOW` | 1 | Výčet zahrnuje pouze čistě instance této třídy a vyloučí všechny instance podtříd, které poskytují vlastnosti, které se v této třídě nenašly. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí volání semisynchronní. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkce vrátí enumerátor pouze s dopředné. Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny. |

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.

`pCtx`\
pro Obvykle je `null`tato hodnota. V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.

`ppEnum`\
mimo Přijme ukazatel na enumerátor.

`authLevel`\
pro Úroveň autorizace.

`impLevel`\
pro Úroveň zosobnění.

`pCurrentNamespace`\
pro Ukazatel na objekt [Služby IWbem](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) , který představuje aktuální obor názvů.

`strUser`\
pro Uživatelské jméno Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`strPassword`\
pro Heslo. Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

`strAuthority`\
pro Název domény uživatele Další informace najdete v tématu funkce [ConnectServerWmi](connectserverwmi.md) .

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

|Konstanta  |Value  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jedné nebo více tříd, které může funkce vracet. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass`neexistuje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartována. Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [Služby IWbem:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .

Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** WMINet_Utils.idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
