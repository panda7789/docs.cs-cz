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
ms.openlocfilehash: 69288e995ec789091bf089368cd9a60f003df86e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122978"
---
# <a name="enumerateclrs-function"></a>EnumerateCLRs – funkce
Poskytuje mechanismus pro vytváření výčtu CLRs v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 pro Identifikátor procesu, ze kterého se má vyčíslit načtené CLRs  
  
 `ppHandleArrayOut`  
 mimo Ukazatel na pole obsahující obslužné rutiny událostí, které se používají k pokračování spuštění modulu CLR. Není zaručeno, že každý popisovač v poli je platný. Je-li tento postup platný, je třeba použít popisovač jako událost pokračování po spuštění pro odpovídající modul runtime umístěný ve stejném indexu `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 mimo Ukazatel na pole řetězců, které určují úplné cesty pro CLRs načtené v procesu.  
  
 `pdwArrayLengthOut`  
 mimo Ukazatel na DWORD, který obsahuje délku rovnoměrné velikosti `ppHandleArrayOut` a `pdwArrayLengthOut`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.  
  
 E_INVALIDARG  
 Buď je `ppHandleArrayOut` nebo `ppStringArrayOut` null, nebo je `pdwArrayLengthOut` null.  
  
 E_OUTOFMEMORY  
 Funkce nemůže přidělit dostatek paměti pro pole popisovač a cesta.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze vytvořit výčet načtených CLRs.  
  
## <a name="remarks"></a>Poznámky  
 Pro cílový proces, který je identifikován `debuggeePID`, funkce vrátí pole cest, `ppStringArrayOut`, na CLRs načtený v procesu; pole obslužných rutin událostí, `ppHandleArrayOut`, které mohou obsahovat událost pokračování-spuštění pro modul CLR ve stejném indexu; a velikost polí `pdwArrayLengthOut`, které určují počet načtených CLRs.  
  
 V operačním systému Windows `debuggeePID` mapuje identifikátor procesu operačního systému.  
  
 Tato funkce přiděluje paměť pro `ppHandleArrayOut` a `ppStringArrayOut`. Chcete-li uvolnit přidělenou paměť, je nutné volat [funkci CloseCLREnumeration –](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md).  
  
 Tuto funkci lze volat s parametrem pole nastaveným na hodnotu null, aby bylo možné vrátit počet CLRs v cílovém procesu. Od tohoto počtu může volající odvodit velikost vyrovnávací paměti, která se vytvoří: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
