---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: bd696752a287a78533d55c0fd3ad9986a32bd180
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111316"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Voláno rozhraním PresentationHost.exe pokaždé, když je přijata zpráva, pokud je vrácena E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
## <a name="parameters"></a>Parametry  
 `pMsg`  
  
 [in] WM_INPUT zpráva odeslaná do okna, které dostává Nezpracovaný vstup.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT:  
  
 S_OK - filtr nemohl zpracovat zprávu a může dojít k dalšímu zpracování.  
  
 S_FALSE - filtr zpracovat tuto zprávu a by mělo dojít k žádné další zpracování.  
  
 E_NOTIMPL – Pokud je tato hodnota se vrátí, [filterinputmessage –](filterinputmessage.md) není volána znovu. To může být vrácena z hostitele aplikace, která interested pouze při poskytování vlastní pokrok a chyba uživatelských rozhraní k PresentationHost.exe není zajímá se předalo PresentationHost.exe nezpracované zprávy o zadávání.  
  
## <a name="remarks"></a>Poznámky  
 PresentationHost.exe je cílem různých nezpracovaná vstupní zařízení, včetně klávesnice, myš a dálková ovládání. V některých případech je závislá na vstupu, který by jinak využívat PresentationHost.exe chování v hostitelské aplikaci. Například hostitelská aplikace může záviset na příjem některé vstupní zprávy k určení, jestli se mají zobrazit prvky konkrétní uživatelského rozhraní.  
  
 Aby hostitelskou aplikaci pro příjem nezbytné vstupní zprávy k poskytování těchto projevů PresentationHost.exe předává odpovídající nezpracované zprávy o zadávání hostované aplikace voláním [filterinputmessage –](filterinputmessage.md).  
  
 Hostované aplikace přijme nezpracované zprávy o zadávání tak, že zaregistrujete sadu nezpracovaná vstupní zařízení (lidské rozhraní) vrácený [getrawinputdevices –](getrawinputdevices.md).  
  
## <a name="see-also"></a>Viz také:

- [WM_INPUT zprávy](/windows/desktop/inputdev/wm-input)
