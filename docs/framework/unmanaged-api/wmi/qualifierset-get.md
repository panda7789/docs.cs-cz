---
title: QualifierSet_Get funkce (Nespravovaný odkaz na rozhraní API)
description: Funkce QualifierSet_Get získá pojmenovaný kvalifikátor.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174885"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get funkce
Získá zadaný pojmenovaný kvalifikátor.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>Parametry

`vFunc`[v] Tento parametr není použit.

`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[v] Název kvalifikátoru, jehož hodnota je požadována.

`lFlags`[v] Vyhrazena. Tento parametr musí být 0.

`pVal`[out] V případě úspěchu správný typ a hodnotu pro kvalifikátor. Pokud funkce selže, `VARIANT` odkazová `pVal` na od se nezmění. Pokud je `null`tento parametr , parametr je ignorován.

`plFlavor`[out] Ukazatel na LONG, který obdrží kvalifikátor chuť bity pro požadované kvalifikátor. Pokud informace o chuti není žádoucí, tento parametr může být `null`.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr není platný. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný kvalifikátor neexistuje. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) metoda.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
