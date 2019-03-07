---
title: EnumerateCLRs – funkce
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7532218728aead72186b5156da87db6d3bc0a8c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469327"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs – funkce
Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [in] Zpracovat identifikátor procesu, ze kterého bude načten CLRs výčtu.  
  
 `ppHandleArrayOut`  
 [out] Ukazatel na pole obsahující obslužné rutiny událostí, které se používají k pokračování spouštění modulu CLR. Každý popisovač pole nemusí být platný. Pokud platné, popisovač je má být použit jako událost pokračovat spuštění pro odpovídající modul runtime umístěný ve stejné index `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Ukazatel na pole řetězců, které určují úplné cesty k CLRs načtené v procesu.  
  
 `pdwArrayLengthOut`  
 [out] Ukazatel na DWORD, který obsahuje délku stejně velké `ppHandleArrayOut` a `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.  
  
 E_INVALIDARG  
 Buď `ppHandleArrayOut` nebo `ppStringArrayOut` má hodnotu null, nebo `pdwArrayLengthOut` má hodnotu null.  
  
 E_OUTOFMEMORY  
 Funkce se nemůže přidělit dostatek paměti pro popisovač a cesta pole.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nepovedlo se vytvořit výčet načíst CLRs.  
  
## <a name="remarks"></a>Poznámky  
 Pro cílový proces, který je identifikován podle `debuggeePID`, funkce vrátí pole cest, `ppStringArrayOut`do CLRs načtené v procesu; pole obslužné rutiny událostí, `ppHandleArrayOut`, který může obsahovat pokračovat spouštěcí událost pro modul CLR ve stejném indexu; a Velikost pole, `pdwArrayLengthOut`, která určuje počet CLRs, které jsou načteny.  
  
 V operačním systému Windows `debuggeePID` mapuje na operační systém zpracovávat identifikátor.  
  
 Paměť pro `ppHandleArrayOut` a `ppStringArrayOut` přidělují touto funkcí. K uvolnění paměti přidělené, musí volat [closeclrenumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Tuto funkci lze volat s oba parametry pole nastavena na hodnotu null, aby mohla vrátit počet CLRs v cílovém procesu. Z tohoto počtu může volající odvodit velikost vyrovnávací paměti, která bude vytvořena: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
