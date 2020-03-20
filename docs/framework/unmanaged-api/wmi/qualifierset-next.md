---
title: QualifierSet_Next funkce (Unmanaged API Reference)
description: Funkce QualifierSet_Next načte další kvalifikátor ve výčtu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174872"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next funkce
Načte další kvalifikátor ve výčtu, který začal s voláním [funkce QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Parametry

`vFunc`[v] Tento parametr není použit.

`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`lFlags`[v] Vyhrazena. Tento parametr musí být 0.

`pstrName`[out] Název kvalifikátoru. Pokud `null`je tento parametr ignorován; v `pstrName` opačném případě by `BSTR` neměl apoukázat na platný nebo dojde k nevracení paměti. Pokud není null, funkce vždy `BSTR` přiděluje nový, když vrátí `WBEM_S_NO_ERROR`.

`pVal`[out] V případě úspěchu, hodnota pro kvalifikátor. Pokud funkce selže, `VARIANT` odkazová `pVal` na od se nezmění. Pokud je `null`tento parametr , parametr je ignorován.

`plFlavor`[out] Ukazatel na LONG, který obdrží kvalifikátor chuť. Pokud informace o chuti není žádoucí, tento parametr může být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Volající nevolal [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Není k dispozici dostatek paměti pro zahájení nového výčtu. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Žádné další kvalifikátory jsou ponechány ve výčtu. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metoda.

Volání `QualifierSet_Next` funkce opakovaně výčet všech kvalifikátorů, `WBEM_S_NO_MORE_DATA`dokud funkce vrátit . Chcete-li výčet ukončit dříve, zavolejte [funkci QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)

Pořadí kvalifikátory vrácené během výčtu není definováno.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
