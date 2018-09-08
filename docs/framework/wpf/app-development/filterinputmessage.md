---
title: FilterInputMessage
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
- FilterInputMessage method [WPF]
ms.assetid: 4d74c6cf-7d1d-49ff-96c1-231340ce54f5
ms.openlocfilehash: 1a22071696ca012968e042e15cd8a9f4b876fd9f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204614"
---
# <a name="filterinputmessage"></a>FilterInputMessage
Voláno rozhraním PresentationHost.exe pokaždé, když je přijata zpráva, pokud je vrácena E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FilterInputMessage( [in] MSG* pMsg ) ;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMsg`  
  
 [in] WM_INPUT zpráva odeslaná do okna, které dostává Nezpracovaný vstup.  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 HODNOTA HRESULT:  
  
 S_OK - filtr nemohl zpracovat zprávu a může dojít k dalšímu zpracování.  
  
 S_FALSE - filtr zpracovat tuto zprávu a by mělo dojít k žádné další zpracování.  
  
 E_NOTIMPL – Pokud je tato hodnota se vrátí, [filterinputmessage –](../../../../docs/framework/wpf/app-development/filterinputmessage.md) není volána znovu. To může být vrácena z hostitele aplikace, která interested pouze při poskytování vlastní pokrok a chyba uživatelských rozhraní k PresentationHost.exe není zajímá se předalo PresentationHost.exe nezpracované zprávy o zadávání.  
  
## <a name="remarks"></a>Poznámky  
 PresentationHost.exe je cílem různých nezpracovaná vstupní zařízení, včetně klávesnice, myš a dálková ovládání. V některých případech je závislá na vstupu, který by jinak využívat PresentationHost.exe chování v hostitelské aplikaci. Například hostitelská aplikace může záviset na příjem některé vstupní zprávy k určení, jestli se mají zobrazit prvky konkrétní uživatelského rozhraní.  
  
 Aby hostitelskou aplikaci pro příjem nezbytné vstupní zprávy k poskytování těchto projevů PresentationHost.exe předává odpovídající nezpracované zprávy o zadávání hostované aplikace voláním [filterinputmessage –](../../../../docs/framework/wpf/app-development/filterinputmessage.md).  
  
 Hostované aplikace přijme nezpracované zprávy o zadávání tak, že zaregistrujete sadu nezpracovaná vstupní zařízení (lidské rozhraní) vrácený [getrawinputdevices –](../../../../docs/framework/wpf/app-development/getrawinputdevices.md).  
  
## <a name="see-also"></a>Viz také  
 [WM_INPUT oznámení](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputmessages/wm_input.asp)
