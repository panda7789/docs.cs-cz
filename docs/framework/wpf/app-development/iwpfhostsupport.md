---
title: IWpfHostSupport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85d4ed09d6c5ca17e148d531e6aac483ff737d51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které jsou hostiteli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsahu prostřednictvím PresentationHost.exe implementace tohoto rozhraní nabízí bod integrace mezi hostitelem a PresentationHost.exe.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]může být hostitelem aplikací, jako jsou webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a ztrátě XAML. K hostiteli [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] vytvořit instanci aplikace [WebBrowser – ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=97911). Pro hostování, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost.exe, která poskytuje hostované [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu pro zobrazení v hostiteli [WebBrowser – ovládací prvek](http://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integrace ve povolené `IWpfHostSupport` umožňuje PresentationHost.exe na:  
  
-   Vyhledejte a zaregistrujte se nezpracovaná vstupní zařízení (zařízení s lidským rozhraní), která je zajímá hostitelskou aplikaci.  
  
-   Přijímat vstupní zprávy z registrovaných nezpracovaná vstupní zařízení a předávání zpráv odpovídající hostitelskou aplikaci.  
  
-   Dotaz hostitelskou aplikaci pro vlastní uživatelská rozhraní průběh a chyby.  
  
> [!NOTE]
>  Toto rozhraní API je určen a podporovaných pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](../../../../docs/framework/wpf/app-development/getrawinputdevices.md)|Umožňuje PresentationHost.exe ke zjištění nezpracovaná vstupní zařízení (zařízení s lidským rozhraní), která je zajímá hostitelskou aplikaci.|  
|[FilterInputMessage](../../../../docs/framework/wpf/app-development/filterinputmessage.md)|Voláno rozhraním PresentationHost.exe vždy, když je přijata zpráva, pokud je vrácen E_NOTIMPL.|  
|[GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)|Ve výchozím nastavení PresentationHost.exe poskytuje svou vlastní průběh nasazení a chyba nasazení uživatelského rozhraní, které se zobrazí při nasazení obsahu WPF.|
