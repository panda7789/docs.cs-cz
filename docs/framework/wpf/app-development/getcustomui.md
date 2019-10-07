---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005708"
---
# <a name="getcustomui"></a>GetCustomUI
Volá se nástrojem PresentationHost. exe, aby se získaly vlastní průběh a chybové zprávy z hostitele, pokud je implementovaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzProgressAssemblyName`  
  
 mimo Ukazatel na sestavení, které obsahuje uživatelské rozhraní průběhu zadané hostitelem.  
  
 `pwzProgressClassName`  
  
 mimo Název třídy, která je uživatelské rozhraní průběhu dodané hostitelem, nejlépe je soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně. Tato třída se nachází v sestavení určeném parametrem `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 mimo Ukazatel na sestavení, které obsahuje uživatelské rozhraní chyby zadané hostitelem.  
  
 `pwzErrorClassName`  
  
 mimo Název třídy, která je uživatelem poskytnutá chyba uživatelského rozhraní, nejlépe je soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně. Tato třída se nachází v sestavení určeném parametrem `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT: ignorováno.  
  
## <a name="remarks"></a>Poznámky  
 Hostitelská aplikace může mít konkrétní motiv, který nemusí splňovat výchozí uživatelská rozhraní PresentationHost. exe. Pokud se jedná o tento případ, hostitelská aplikace může implementovat [GetCustomUI](getcustomui.md) a vrátit tak průběh a chybná uživatelská rozhraní PresentationHost. exe. PresentationHost. exe bude před použitím výchozích uživatelských rozhraní vždy volat [GetCustomUI](getcustomui.md) .  
  
 Tato funkce se volá jednou během inicializace PresentationHost.  
  
## <a name="see-also"></a>Viz také:

- [IWpfHostSupport](iwpfhostsupport.md)
