---
title: "CreateVersionStringFromModule – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateVersionStringFromModule
api_location: dbgshim.dll
api_type: COM
f1_keywords: CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b8fb3cdb0bb2d7536c1c1514d4202271411d112
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="createversionstringfrommodule-function"></a>CreateVersionStringFromModule – funkce
Vytvoří řetězec verze z běžných language runtime (CLR) cestu Cílový proces.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pidDebuggee`  
 [v] Identifikátor procesu, ve kterém je načtena cíl CLR.  
  
 `szModuleName`  
 [v] Úplná nebo relativní cesta k cílovému CLR, který je načten do procesu.  
  
 `pBuffer`  
 [out] Vrátí velikost vyrovnávací paměti pro ukládání řetězec verze pro cíl CLR.  
  
 `cchBuffer`  
 [v] Velikost `pBuffer`.  
  
 `pdwLength`  
 [out] Délka řetězce verze vrácený `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Řetězec verze pro cíl CLR byla úspěšně vrácena v `pBuffer`.  
  
 E_INVALIDARG  
 `szModuleName`je null, nebo zadejte `pBuffer` nebo `cchBuffer` má hodnotu null. `pBuffer`a `cchBuffer` musí být null ani nesmí být nulová.  
  
 HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)  
 `pdwLength`je větší než `cchBuffer`. Pokud jste pro obě uplynulo hodnotu null. to může být očekávaný výsledek `pBuffer` a `cchBuffer`a dotaz velikost vyrovnávací paměti nezbytné pomocí `pdwLength`.  
  
 HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)  
 `szModuleName`neobsahuje cestu k platný CLR v tento cílový proces.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 `pidDebuggee`neodkazuje na platný procesu nebo jiné chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce přijímá CLR proces, který je určený podle `pidDebuggee` a řetězec cesty, která je zadána `szModuleName`. Řetězec verze se vrátí ve vyrovnávací paměti, `pBuffer` odkazuje na. Tento řetězec je plné krytí funkce uživateli; To znamená neexistuje žádný vnitřní význam v samotné řetězec verze. Se používá pouze v kontextu této funkce a [createdebugginginterfacefromversion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md).  
  
 Tato funkce by měla být volána dvakrát. Při volání ji poprvé, předat hodnotu null pro obě `pBuffer` a `cchBuffer`. Pokud jste to provést, velikost vyrovnávací paměti, která je potřebná pro `pBuffer` , vrátí se `pdwLength`. Můžete pak zavolejte funkci znovu a předávat vyrovnávací paměť v `pBuffer` a jeho velikost v `cchBuffer`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
