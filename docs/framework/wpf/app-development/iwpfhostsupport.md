---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 074167111b78edc517dda019465260d0acd54737
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376010"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které hostují [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu prostřednictvím PresentationHost.exe implementace tohoto rozhraní stanovit bodů integrace mezi hostitelem a PresentationHost.exe.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] může být hostitelem aplikací, jako jsou webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsah, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volný XAML. K hostiteli [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsah, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace vytvořit instanci [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Zajistit také jejich hostování, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost.exe, která poskytuje hostovanou [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] hostitele pro zobrazení v obsahu [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integrace zajišťuje `IWpfHostSupport` umožňuje PresentationHost.exe na:  
  
-   Zjistit a zaregistrovat nezpracovaná vstupní zařízení (lidské rozhraní), které je hostitelskou aplikaci zájem.  
  
-   Přijímá vstupní zprávy z registrovaných nezpracovaná vstupní zařízení a předávání zpráv příslušné hostitelské aplikace.  
  
-   Dotaz na hostitelskou aplikaci pro vlastní uživatelská rozhraní průběhu a chyba.  
  
> [!NOTE]
>  Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umožňuje PresentationHost.exe zjišťování zařízení nezpracovaná vstupní (lidské rozhraní zařízení), které hostitelskou aplikaci zájem.|  
|[FilterInputMessage](filterinputmessage.md)|Voláno rozhraním PresentationHost.exe pokaždé, když je přijata zpráva, pokud je vrácena E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Ve výchozím nastavení PresentationHost.exe poskytuje vlastní průběh nasazení a chyba nasazení uživatelská rozhraní, které se zobrazují při nasazení obsahu WPF.|
