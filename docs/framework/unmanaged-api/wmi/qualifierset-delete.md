---
title: QualifierSet_Delete funkce (Nespravovaný odkaz na rozhraní API)
description: Funkce QualifierSet_Delete odstraní kvalifikátor podle názvu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174898"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete funkce
Odstraní zadaný kvalifikátor podle názvu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[v] Tento parametr není použit.

`ptr`[v] Ukazatel na instanci [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[v] Název kvalifikátoru k odstranění.

## <a name="return-value"></a>Návratová hodnota

Následující hodnoty vrácené touto funkcí jsou definovány v souboru *hlavičky WbemCli.h,* nebo je můžete definovat jako konstanty v kódu:

|Trvalé  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `wszName` není platný. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Odstranění tohoto kvalifikátoru je nezákonné. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Zadaný kvalifikátor nebyl nalezen. |
|`WBEM_S_NO_ERROR` | 0 | Volání funkce bylo úspěšné.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Místní přepsání bylo odstraněno a původní kvalifikátor z nadřazeného objektu obnovil obor. |

## <a name="remarks"></a>Poznámky

Tato funkce zalomí volání [metody IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)

Z důvodu pravidel šíření kvalifikátoru může být určitý kvalifikátor zděděn z jiného objektu a pouze přepsán v aktuální třídě nebo instanci. V tomto případě `QualifierSet_Delete` metoda obnoví kvalifikátor na původní zděděnou hodnotu. Funkce v tomto případě vrátí `WBEM_S_RESET_TO_DEFAULT`stavový kód .

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.idl  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také

- [Čítače služby WMI a výkonu (nespravovaný odkaz na rozhraní API)](index.md)
