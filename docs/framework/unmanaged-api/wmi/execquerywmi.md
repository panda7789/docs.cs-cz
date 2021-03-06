---
title: ExecQueryWmi – funkce (Reference nespravovaného rozhraní API)
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
ms.openlocfilehash: 3c6ea58eca5ac635893a24b57ade261e04a69721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130438"
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
pro Řetězec s platným dotazovacím jazykem, který podporuje Správa systému Windows. Musí být "WQL", zkratka pro jazyk WQL (WMI Query Language).

`strQuery`\
pro Text dotazu Tento parametr nelze `null`.

`lFlags`\
pro Kombinace příznaků, které mají vliv na chování této funkce. Následující hodnoty jsou definovány v souboru hlaviček *WbemCli. h* nebo je můžete definovat jako konstanty v kódu:

| Konstanta | Hodnota  | Popis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Pokud je tato funkce nastavena, funkce načte změněné kvalifikátory uložené v lokalizovaném oboru názvů národního prostředí aktuálního připojení. <br/> Pokud není nastaveno, funkce načte pouze kvalifikátory uložené v bezprostředním oboru názvů. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Příznak způsobí volání semisynchronní. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkce vrátí enumerátor pouze s dopředné. Čítače pouze s dopředně jsou obvykle rychlejší a využívají méně paměti než konvenční enumerátory, ale neumožňují volání [klonování](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0,8 | Rozhraní WMI uchovává ukazatele na objekty ve výčtu, dokud nebudou uvolněny. |
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zajistí, že všechny vrácené objekty mají v nich dostatek informací, aby nebyly `null`systémové vlastnosti, například **__PATH**, **__RELPATH**a **__SERVER**. |
| `WBEM_FLAG_PROTOTYPE` | odst | Tento příznak se používá pro vytváření prototypů. Nespustí dotaz a místo toho vrátí objekt, který vypadá jako typický objekt výsledku. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Způsobuje přímý přístup k poskytovateli pro třídu určenou bez ohledu na její nadřazenou třídu nebo žádné podtřídy. |

Doporučené příznaky jsou `WBEM_FLAG_RETURN_IMMEDIATELY` a `WBEM_FLAG_FORWARD_ONLY` pro nejlepší výkon.

`pCtx`\
pro Tato hodnota je obvykle `null`. V opačném případě se jedná o ukazatel na instanci [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) , kterou může použít poskytovatel, který poskytuje požadované třídy.

`ppEnum`\
mimo Pokud nedojde k žádné chybě, přijme ukazatel na enumerátor, který umožňuje volajícímu načíst instance v sadě výsledků dotazu. Dotaz může mít sadu výsledků s nulovými instancemi. Další informace najdete v části [poznámky](#remarks) .

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

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Uživatel nemá oprávnění k zobrazení jedné nebo více tříd, které může funkce vracet. |
| `WBEM_E_FAILED` | 0x80041001 | Došlo k neurčené chybě. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Dotaz obsahoval chybu syntaxe. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Požadovaný dotazovací jazyk není podporován. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Dotaz je příliš složitý. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | K dokončení této operace není k dispozici dostatek paměti. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Služba WMI byla pravděpodobně zastavena a restartována. Znovu zavolejte [ConnectServerWmi](connectserverwmi.md) . |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Propojení vzdáleného volání procedur (RPC) mezi aktuálním procesem a rozhraním WMI se nezdařilo. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Dotaz určuje třídu, která neexistuje. |
| `WBEM_S_NO_ERROR` | 0,8 | Volání funkce bylo úspěšné.  |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání metody [Služby IWbem:: ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) .

Tato funkce zpracuje dotaz zadaný v parametru `strQuery` a vytvoří enumerátor, přes který volající může získat přístup k výsledkům dotazu. Enumerátor je ukazatel na rozhraní [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) ; výsledky dotazu jsou instance objektů třídy, které jsou k dispozici prostřednictvím rozhraní [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Existují omezení počtu `AND` a `OR` klíčová slova, která lze použít v dotazech jazyka WQL. Velký počet klíčových slov jazyka WQL používaných ve složitých dotazech může způsobit, že rozhraní WMI vrátí kód chyby `WBEM_E_QUOTA_VIOLATION` (nebo 0x8004106c) jako hodnotu `HRESULT`. Omezení klíčových slov jazyka WQL závisí na tom, jak je dotaz složitý.

Pokud volání funkce neproběhne úspěšně, můžete získat další informace o chybě voláním funkce [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** WMINet_Utils. idl

**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (Reference nespravovaného rozhraní API)](index.md)
