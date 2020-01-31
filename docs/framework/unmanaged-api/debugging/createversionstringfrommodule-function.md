---
title: CreateVersionStringFromModule – funkce
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
ms.openlocfilehash: 609d6e47c951aa104cb23084b65e98827a6851f1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789181"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule – funkce
Vytvoří řetězec verze z cesty modulu CLR (Common Language Runtime) v cílovém procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pidDebuggee`  
 pro Identifikátor procesu, ve kterém je načten cílový modul CLR.  
  
 `szModuleName`  
 pro Úplná nebo relativní cesta k cílovému modulu CLR, který je načten do procesu.  
  
 `pBuffer`  
 mimo Návratová vyrovnávací paměť pro uložení řetězce verze pro cílový CLR.  
  
 `cchBuffer`  
 pro Velikost `pBuffer`.  
  
 `pdwLength`  
 mimo Délka řetězce verze vráceného funkcí `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Řetězec verze pro cílový modul CLR byl úspěšně vrácen v `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` je null nebo buď `pBuffer` nebo `cchBuffer`, má hodnotu null. `pBuffer` a `cchBuffer` musí mít hodnotu null nebo být prázdné.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` je větší než `cchBuffer`. To může být očekávaný výsledek, pokud jste předali hodnotu null pro `pBuffer` i `cchBuffer`a dotazováni jste na potřebnou velikost vyrovnávací paměti pomocí `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` neobsahuje cestu k platnému modulu CLR v cílovém procesu.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 `pidDebuggee` neodkazuje na platný proces nebo jiné selhání.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce přijímá proces CLR identifikovaný `pidDebuggee` a cestu k řetězci, která je určena `szModuleName`. Řetězec verze je vrácen do vyrovnávací paměti, na kterou `pBuffer` odkazuje. Tento řetězec je neprůhledný pro uživatele funkce. To znamená, že v samotném řetězci verze není žádný vnitřní význam. Používá se výhradně v kontextu této funkce a [funkci CreateDebuggingInterfaceFromVersion –](createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Tato funkce by měla být volána dvakrát. Při prvním volání předejte hodnotu null pro `pBuffer` i `cchBuffer`. Když to uděláte, v `pdwLength`se vrátí velikost vyrovnávací paměti nutné pro `pBuffer`. Potom můžete zavolat funkci podruhé a předat vyrovnávací paměť v `pBuffer` a její velikosti v `cchBuffer`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
