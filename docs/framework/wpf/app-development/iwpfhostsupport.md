---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964787"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] hostují obsah prostřednictvím PresentationHost. exe, implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]aplikace, jako jsou například webové prohlížeče [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] , mohou hostovat [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] obsah, včetně a volného kódu XAML. Pro hostování [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] obsahu aplikace vytvoří instanci [ovládacího prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Pro hostování [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] vytvoří instanci PresentationHost. exe, která poskytuje hostovanému [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] obsahu hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integrace povolená pomocí `IWpfHostSupport` nástroje umožňuje PresentationHost. exe:  
  
- Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.  
  
- Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.  
  
- Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.  
  
> [!NOTE]
> Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.|  
|[FilterInputMessage](filterinputmessage.md)|Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.|
