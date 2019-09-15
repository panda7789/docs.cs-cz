---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991381"
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
  
 mimo Název třídy, která je uživatelsky dodaným uživatelským rozhraním průběhu, nejlépe [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] je soubor <xref:System.Windows.Controls.Page> s prvkem nejvyšší úrovně. Tato třída se nachází v sestavení určeném parametrem `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 mimo Ukazatel na sestavení, které obsahuje uživatelské rozhraní chyby zadané hostitelem.  
  
 `pwzErrorClassName`  
  
 mimo Název třídy, která je uživatelem poskytnutá chyba uživatelského rozhraní, nejlépe je soubor XAML s <xref:System.Windows.Controls.Page> prvkem nejvyšší úrovně. Tato třída se nachází v sestavení určeném parametrem `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HRESULT Přeskočen.  
  
## <a name="remarks"></a>Poznámky  
 Hostitelská aplikace může mít konkrétní motiv, který nemusí splňovat výchozí uživatelská rozhraní PresentationHost. exe. Pokud se jedná o tento případ, hostitelská aplikace může implementovat [GetCustomUI](getcustomui.md) a vrátit tak průběh a chybná uživatelská rozhraní PresentationHost. exe. PresentationHost. exe bude před použitím výchozích uživatelských rozhraní vždy volat [GetCustomUI](getcustomui.md) .  
  
 Tato funkce se volá jednou během inicializace PresentationHost.  
  
## <a name="see-also"></a>Viz také:

- [IWpfHostSupport](iwpfhostsupport.md)
