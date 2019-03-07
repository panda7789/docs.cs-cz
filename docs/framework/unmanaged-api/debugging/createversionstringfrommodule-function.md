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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ed8b85475dc7327c1aac6f920aba627215e27c7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492020"
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule – funkce
Vytvoří řetězec verze z společná cesta modulu runtime (CLR) jazyka v cílovém procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Identifikátor procesu, ve které je cílem CLR načten.  
  
 `szModuleName`  
 [in] Úplná nebo relativní cesta k cíli CLR, který je načten do procesu.  
  
 `pBuffer`  
 [out] Vrátí vyrovnávací paměť pro ukládání řetězce verze pro cíl CLR.  
  
 `cchBuffer`  
 [in] Velikost `pBuffer`.  
  
 `pdwLength`  
 [out] Délka řetězce verze vrácené `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Řetězec verze pro cíl modulu CLR byla úspěšně vrácena v `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName` je null nebo buď `pBuffer` nebo `cchBuffer` má hodnotu null. `pBuffer` a `cchBuffer` musí být null nebo jinou hodnotu než null.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength` je větší než `cchBuffer`. Pokud jste u obou prošly hodnotu null, může dojít očekávaný výsledek `pBuffer` a `cchBuffer`, Power pivotu a dotazované nezbytné vyrovnávací paměť s použitím `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName` neobsahuje cestu k platné CLR v cílovém procesu.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 `pidDebuggee` neodkazuje na platný proces nebo jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce přijme procesu CLR, který je identifikován `pidDebuggee` a řetězec cesty, která je zadána `szModuleName`. Řetězec verze je vrácen ve vyrovnávací paměti, která `pBuffer` odkazuje na. Tento řetězec je neprůhledný funkce uživatele. To znamená, že neexistuje žádný vnitřní význam v samotný řetězec verze. Používá se pouze v rámci této funkce a [createdebugginginterfacefromversion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Tato funkce by měla být volána dvakrát. Při volání ji první, předat hodnotu null pro obě `pBuffer` a `cchBuffer`. Pokud to provedete, velikost vyrovnávací paměti pro `pBuffer` , vrátí se `pdwLength`. Můžete pak zavolejte funkci znovu a předejte vyrovnávací paměti v `pBuffer` a jeho velikost v `cchBuffer`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
