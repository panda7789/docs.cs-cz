---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: af51a0d76ac080017f58ac8fc3acca86c23fb480
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474862"
---
# <a name="getcustomui"></a>GetCustomUI
Voláno rozhraním PresentationHost.exe získat vlastní pokrok a chybové zprávy z hostitele, pokud implementovaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzProgressAssemblyName`  
  
 [out] Ukazatel, který obsahuje uživatelské rozhraní poskytované hostitele průběh sestavení.  
  
 `pwzProgressClassName`  
  
 [out] Název třídy, který je zadán hostitel průběh uživatelského rozhraní, ideálně [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] soubor s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně. Tato třída se nachází v sestavení, která je zadána `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Ukazatel na sestavení, která obsahuje hostitele zadanou chybovou uživatelské rozhraní.  
  
 `pwzErrorClassName`  
  
 [out] Název třídy, který je zadán hostitel chyba uživatele pokud možno rozhraní soubor XAML s <xref:System.Windows.Controls.Page> je jeho element nejvyšší úrovně. Tato třída se nachází v sestavení, která je zadána `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT: Ignorovat.  
  
## <a name="remarks"></a>Poznámky  
 Hostitelská aplikace může mít konkrétní motivu, který nemusí vyhovovat vaší PresentationHost.exe výchozí uživatelská rozhraní. Pokud je to tento případ, můžete implementovat hostitelskou aplikaci [GetCustomUI –](getcustomui.md) vrátit průběh a Chyba uživatelského rozhraní pro PresentationHost.exe. Vždy zavolá PresentationHost.exe [GetCustomUI –](getcustomui.md) před použitím jeho výchozí uživatelská rozhraní.  
  
 Tato funkce je volána jednou během inicializace PresentationHost společnosti.  
  
## <a name="see-also"></a>Viz také:
- [IWpfHostSupport](iwpfhostsupport.md)
