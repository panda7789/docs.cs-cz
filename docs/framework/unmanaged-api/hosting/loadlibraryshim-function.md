---
title: LoadLibraryShim – funkce
ms.date: 03/30/2017
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
ms.openlocfilehash: 4b270c36bdbea9c8d81915eba424cae1054ce7d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008531"
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim – funkce
Načte zadanou verzi knihovny DLL, která je součástí .NET Framework Distribuovatelný balíček.  
  
 Tato funkce se už nepoužívá v .NET Framework 4. Místo toho použijte metodu [ICLRRuntimeInfo:: LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szDllName`  
 pro Řetězec zakončený nulou, který představuje název knihovny DLL, která má být načtena z knihovny .NET Framework.  
  
 `szVersion`  
 pro Řetězec zakončený nulou, který představuje verzi knihovny DLL, která má být načtena. Pokud `szVersion` je null, verze vybraná pro načtení je nejnovější verze zadané knihovny DLL, která je menší než verze 4. To znamená, že všechny verze, které se rovnají nebo jsou vyšší než verze 4, jsou ignorovány `szVersion` , pokud je hodnota null a není-li nainstalována žádná verze, která je nižší než verze 4, knihovna DLL se nepodařilo načíst. K tomu je potřeba zajistit, aby instalace .NET Framework 4 neovlivnila stávající aplikace nebo komponenty. Podívejte se na záznam [v rámci proc SxS a migrace rychlé zprovoznění](https://devblogs.microsoft.com/dotnet/in-proc-sxs-and-migration-quick-start/) na blogu týmu CLR.  
  
 `pvReserved`  
 Vyhrazeno pro budoucí použití.  
  
 `phModDll`  
 mimo Ukazatel na popisovač modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Description|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|CLR_E_SHIM_RUNTIMELOAD|Načítání `szDllName` vyžaduje načtení modulu CLR (Common Language Runtime) a potřebnou verzi modulu CLR nelze načíst.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se používá k načtení knihoven DLL, které jsou součástí .NET Framework Distribuovatelný balíček. Nenačítá uživatelem generované knihovny DLL.  
  
> [!NOTE]
> Počínaje verzí 2,0 .NET Framework, načtení souboru Fusion. dll způsobí načtení modulu CLR. Důvodem je, že funkce v Fusion. dll jsou nyní obálky, jejichž implementace jsou poskytovány modulem runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
