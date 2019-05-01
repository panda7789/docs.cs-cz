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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77164f9d8a1641ba37fa504d09d77ec6aecc3db5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965807"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion – funkce pro technologii Silverlight
Přijímá běžné modulu CLR verze řetězec jazyka, který je vrácen z [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu (obvykle [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDebuggeeVersion`  
 [in] Řetězec verze modulu CLR cílové laděného procesu, který je vrácený [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).  
  
 `ppCordb`  
 [out] Ukazatel na ukazatel na objekt modelu COM (`IUnknown`). Tento objekt přetypovat [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu před jeho vrácením.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 `ppCordb` odkazuje na platný objekt, který implementuje [icordebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní.  
  
 E_INVALIDARG  
 Buď `szDebuggeeVersion` nebo `ppCordb` má hodnotu null.  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 Nelze najít komponentu, která je nezbytná pro ladění CLR. To znamená, že knihovna mscordbi.dll nebo mscordaccore.dll nebyl nalezen ve stejném adresáři jako cíl CoreCLR.dll.  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 Knihovna mscordbi.dll nebo mscordaccore.dll není stejná verze jako cíl CoreCLR.dll.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nejde vrátit [icordebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní, která je vrácena poskytuje funkce pro ladění spravovaného kódu, který je spuštěn modul CLR a připojení k modulu CLR v cílovém procesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
