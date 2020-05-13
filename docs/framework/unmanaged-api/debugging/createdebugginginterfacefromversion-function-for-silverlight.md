---
title: CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208621"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight

Přijímá řetězec verze modulu CLR (Common Language Runtime), který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md)a vrací odpovídající rozhraní ladicího programu (obvykle [ICorDebug](icordebug-interface.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametry  

 `szDebuggeeVersion`\
 pro Řetězec verze modulu CLR v cílovém laděného procesu, který je vrácen [funkcí CreateVersionStringFromModule –](createversionstringfrommodule-function.md).  
  
 `ppCordb`\
 mimo Ukazatel na ukazatel na objekt modelu COM ( `IUnknown` ). Tento objekt bude převeden na objekt [ICorDebug](icordebug-interface.md) před jeho vrácením.  
  
## <a name="return-value"></a>Návratová hodnota

 `S_OK`\
 `ppCordb`odkazuje na platný objekt, který implementuje rozhraní [rozhraní ICorDebug](icordebug-interface.md) .  
  
 `E_INVALIDARG`\
 Buď `szDebuggeeVersion` nebo `ppCordb` je null.  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 Nelze nalézt komponentu, která je nezbytná pro ladění CLR. _Mscordbi. dll_ nebo _mscordaccore. dll_ se nepodařilo najít ve stejném adresáři jako cílový CoreCLR. dll.  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 Mscordbi. dll nebo mscordaccore. dll není stejná jako verze cílového CoreCLR. dll.  
  
 `E_FAIL`(nebo jiné `E_` návratové kódy) \
 Nelze vrátit [rozhraní ICorDebug](icordebug-interface.md).  
  
## <a name="remarks"></a>Poznámky

 Rozhraní, které je vráceno, poskytuje zařízení pro připojení k CLR v cílovém procesu a ladění spravovaného kódu, který je spuštěn modul CLR.  
  
## <a name="requirements"></a>Požadavky

 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
